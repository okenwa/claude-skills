# DirectAdmin Hosting Automation

Automate website setup on DirectAdmin reseller accounts using data from Google Sheets, with WordPress installation and Trello tracking.

## Triggers
- "setup website", "create hosting", "directadmin", "provision account", "new hosting account", "wordpress", "trello update"

## Capabilities

### From Google Sheets
- Read client/website data
- Validate entries before processing
- Update status after completion

### DirectAdmin Operations
- Create user accounts
- Add domains
- Set up email accounts
- Install SSL (Let's Encrypt)
- Apply hosting packages
- Manage DNS records
- Create databases

## Required Environment Variables

```env
# DirectAdmin
DIRECTADMIN_URL=https://server.example.com:2222
DIRECTADMIN_USER=reseller_username
DIRECTADMIN_PASS=reseller_password

# Google Sheets (Service Account)
GOOGLE_SERVICE_ACCOUNT_EMAIL=bot@project.iam.gserviceaccount.com
GOOGLE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n..."
GOOGLE_SHEET_ID=1abc123...

# Trello
TRELLO_API_KEY=your_api_key
TRELLO_TOKEN=your_token
TRELLO_BOARD_ID=your_board_id
```

## Sheet Structure

Expected columns:
| Column | Description | Required |
|--------|-------------|----------|
| domain | Domain name (e.g., example.com) | Yes |
| username | DA username (auto-generated if empty) | No |
| email | Contact email | Yes |
| package | Hosting package name | Yes |
| password | Account password (auto-generated if empty) | No |
| wordpress | Install WordPress (yes/no) | No |
| trello | Create Trello card (yes/no) | No |
| ssl | Install SSL (yes/no) | No |
| create_email | Create info@ email (yes/no) | No |
| status | Processing status | Auto |

## DirectAdmin API Reference

### Create User Account
```bash
curl -X POST "https://server:2222/CMD_API_ACCOUNT_USER" \
  -u "reseller:password" \
  -d "action=create" \
  -d "username=newuser" \
  -d "email=user@example.com" \
  -d "passwd=SecurePass123" \
  -d "passwd2=SecurePass123" \
  -d "domain=example.com" \
  -d "package=basic" \
  -d "notify=yes"
```

### Add Domain
```bash
curl -X POST "https://server:2222/CMD_API_DOMAIN" \
  -u "user:password" \
  -d "action=create" \
  -d "domain=newdomain.com"
```

### Create Email Account
```bash
curl -X POST "https://server:2222/CMD_API_POP" \
  -u "user:password" \
  -d "action=create" \
  -d "domain=example.com" \
  -d "user=info" \
  -d "passwd=EmailPass123"
```

### Install SSL
```bash
curl -X POST "https://server:2222/CMD_API_SSL" \
  -u "user:password" \
  -d "domain=example.com" \
  -d "action=save" \
  -d "type=letsencrypt"
```

### Create Database
```bash
curl -X POST "https://server:2222/CMD_API_DATABASES" \
  -u "user:password" \
  -d "action=create" \
  -d "name=dbname" \
  -d "user=dbuser" \
  -d "passwd=DbPass123"
```

## Workflow

1. **Read Sheet** - Fetch rows with status = empty or "pending"
2. **Validate** - Check domain format, required fields
3. **Generate** - Auto-create username/password if needed
4. **Provision** - Create account via DirectAdmin API
5. **Setup** - Add domain, SSL, email as configured
6. **Update Sheet** - Mark status as "completed" or "error"
7. **Notify** - Send credentials to client email

## Usage Example

User: "Setup websites from the hosting sheet"

Bot will:
1. Read pending entries from Google Sheet
2. For each row:
   - Create DirectAdmin account
   - Set up domain
   - Install SSL
   - Create default email (info@domain)
3. Update sheet with completion status
4. Email credentials to each client

## Error Handling

- Domain already exists → Skip, mark as "exists"
- Invalid domain format → Mark as "invalid"
- API failure → Mark as "error: [reason]"
- Retry failed operations on next run
