# N8N Automation Workflows

Welcome to my N8N Automation repository! 🚀 This project contains a collection of sophisticated automation workflows using n8n to integrate various applications and APIs.

## 📋 Table of Contents

- [About](#about)
- [Workflows Included](#workflows-included)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Architecture](#architecture)
- [Support](#support)

## 🎯 About

This repository contains automated n8n workflows designed for:
- Processing form submissions
- Filtering and processing data
- Extracting information via APIs
- Integrating Anthropic Chat for artificial intelligence
- Inserting data into databases
- Sending automatic messages
- Updating data rows

The workflows use a modular approach with logical conditions (if/else) and advanced data handling.

## 📦 Workflows Included

### 1. **Form Submission & Processing Workflow**
Complete workflow for processing form submissions with the following steps:
- Trigger: Form submission
- Data filtering
- Information extraction
- Conditional branching (true/false/manual)
- Integration with Anthropic Chat Model
- Database row insertion
- Message sending

**Use cases**: Automate customer request processing, registrations, or surveys.

### 2. **AI-Powered Chat Workflow**
Workflow triggered when receiving a chat message:
- Trigger: Chat message received
- Anthropic Chat Model integration
- Simple memory management
- Data fetching (fetch Q&A)
- Database row insertion
- Automatic responses

**Use cases**: Intelligent chatbot with persistent memory and database search.

### 3. **Advanced Data Processing Workflow**
Workflow with advanced conditional logic:
- Multiple conditions (if/then/else)
- Manual instructions as an option
- Iterative loops
- Parallel processing

**Use cases**: Complex workflows requiring sophisticated business logic.

## ✅ Prerequisites

- **n8n** (self-hosted or cloud) - [Installation](https://docs.n8n.io/getting-started/)
- **Anthropic Account** - To use Claude API
- **Supported Databases**: 
  - PostgreSQL
  - MySQL
  - MongoDB
  - Google Sheets (via API)
  - Other n8n integrations
- **Node.js** (if self-hosted) - v14.0.0 or higher

## 🚀 Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/hamzaaithammou-tech/N8N-automation.git
cd N8N-automation
```

### Step 2: Set Up n8n

If you are using n8n self-hosted:

```bash
npm install -g n8n
n8n start
```

Then access `http://localhost:5678`

### Step 3: Import Workflows

1. In the n8n interface, go to **Workflows**
2. Click on **Import from file** or **Import from URL**
3. Select the JSON workflow files from this repository
4. The workflows will be imported with their configuration

## ⚙️ Configuration

### Environment Variables

Create a `.env` file at the root of the project:

```env
# Anthropic API
ANTHROPIC_API_KEY=your_api_key_here

# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=automation_db
DB_USER=postgres
DB_PASSWORD=your_password

# Webhook (if applicable)
WEBHOOK_URL=https://your-domain.com/webhook

# n8n Settings
N8N_WEBHOOK_TUNNEL_URL=https://your-domain.com
```

### Node Configuration

Each workflow requires configuring:

1. **Anthropic Chat Model**: 
   - Add your Anthropic API key
   - Configure the model (claude-opus, claude-sonnet, etc.)

2. **Database**: 
   - Configure your DB connection
   - Modify SQL queries according to your schema

3. **Triggers**: 
   - Configure webhooks or application triggers
   - Adjust filters if necessary

## 📖 Usage

### Manually Trigger a Workflow

```bash
curl -X POST http://localhost:5678/webhook/my-webhook-name \
  -H "Content-Type: application/json" \
  -d '{"key": "value"}'
```

### Monitor Execution

- Go to the **Executions** tab in n8n
- Check logs and input/output data
- Check the **Evaluations** tab to analyze errors

### Publish a Workflow

1. Click the **Publish** button (top right)
2. The workflow becomes active and responsive to triggers
3. Check the publication status and statistics

## 🏗️ Architecture

### General Flow

```
Trigger (Webhook/Chat/Form)
    ↓
Data Filter & Validation
    ↓
Information Extraction
    ↓
Conditional Logic (If/Else)
    ↓
AI Call (Anthropic Chat Model)
    ↓
Result Processing
    ↓
Database Storage
    ↓
User Notification/Response
```

### Main Integrations

| Integration | Usage |
|-------------|-------|
| Anthropic Chat | Intelligent processing and AI responses |
| Database | Persistent data storage |
| Webhooks | External workflow triggering |
| External APIs | Data retrieval and synchronization |

## 📊 Execution Examples

### Example 1: Form Submission
```json
{
  "input": {
    "name": "Hamza",
    "email": "hamza@example.com",
    "message": "I would like to learn more"
  },
  "output": {
    "status": "processed",
    "response": "Thank you for your interest! We will contact you soon.",
    "row_inserted": true
  }
}
```

### Example 2: AI Chat
```json
{
  "input": {
    "sessionId": "39604...",
    "chatinput": "What are your opening hours?",
    "action": "sendMessage"
  },
  "output": {
    "output": "We are open from 9 AM to 6 PM Monday through Friday..."
  }
}
```

## 🔐 Security

- ✅ API keys are stored in environment variables
- ✅ Webhooks should be protected by authentication if necessary
- ✅ Use HTTPS for connections in production
- ✅ Limit permissions on database accounts
- ✅ Enable audit logs to track executions

## 🐛 Troubleshooting

### Workflow doesn't trigger
- Check that the webhook is active (button next to the node)
- Check logs in **Executions > Failed**
- Make sure the webhook URL is correct

### Database connection errors
- Verify connection parameters (.env)
- Ensure the database is accessible
- Check database user permissions

### Anthropic API issues
- Verify your API key and quota
- Check Anthropic API status
- Review execution logs for error details

## 📚 Additional Documentation

- [n8n Documentation](https://docs.n8n.io/)
- [Anthropic Claude API](https://docs.anthropic.com/)
- [n8n Workflows Best Practices](https://docs.n8n.io/workflows/best-practices/)

## 🤝 Contributing

Contributions are welcome! To contribute:

1. **Fork** the repository
2. Create a branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a **Pull Request**

### Guidelines
- Document your workflows in this README
- Export workflows as JSON before pushing
- Thoroughly test before submitting a PR
- Follow existing naming conventions

## 📈 Future Improvements

- [ ] Add webhook authentication
- [ ] Integrate other LLMs (OpenAI, Cohere)
- [ ] Add automated tests
- [ ] Create monitoring dashboard
- [ ] Implement rate limiting
- [ ] Add advanced error handling

## 📞 Support

For questions or issues:
- Open an **[Issue](https://github.com/hamzaaithammou-tech/N8N-automation/issues)** on GitHub
- Check the **[Discussions](https://github.com/hamzaaithammou-tech/N8N-automation/discussions)**
- Contact me via email: hamza00bb@gmail.com

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## ⭐ Support This Project

If this repository has been useful to you, feel free to give it a ⭐!

---

**Created with ❤️ by [Hamza Aithammou](https://github.com/hamzaaithammou-tech)**
