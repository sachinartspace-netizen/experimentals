# Claude Models in VS Code - Troubleshooting Guide

## Issue: Claude Models Not Available in VS Code

If you're seeing a message like "Contact your admin - you don't have access to these models" when trying to use Claude models (like Claude Sonnet 4.6) in VS Code, here's what you need to know:

### Understanding the Issue

**GitHub Copilot Pro and Claude are separate services:**
- GitHub Copilot Pro does not include access to Claude models
- GitHub Copilot uses OpenAI's models (GPT-4, GPT-3.5, etc.)
- Claude models are developed by Anthropic, a different company

### Solutions

#### Option 1: Use Claude Through Official Channels

To access Claude models in VS Code, you need one of these:

1. **Anthropic API Access**
   - Sign up at https://console.anthropic.com/
   - Get an API key
   - Use a VS Code extension that supports Anthropic API (like "Claude Dev" or similar extensions)

2. **Claude Pro Subscription**
   - Subscribe at https://claude.ai/
   - Provides access to Claude through the web interface
   - Some extensions may support Claude Pro authentication

3. **Amazon Bedrock**
   - Access Claude models through AWS Bedrock
   - Requires AWS account and appropriate permissions
   - Use VS Code extensions that support Bedrock

#### Option 2: Check Your Organization's Access

If you're part of an organization:
- Check with your admin about Anthropic API access
- Your organization may need to set up an Anthropic account
- GitHub Copilot Business/Enterprise does not automatically include Claude

#### Option 3: Verify Extension Compatibility

Make sure you're using the right extension:
- Check if your VS Code extension actually supports Claude models
- Some extensions claim to support multiple models but require separate API keys
- Read the extension documentation carefully

### Common Misconceptions

❌ **GitHub Copilot Pro includes Claude models** - This is incorrect
✅ **You need separate Anthropic API access for Claude**

❌ **Student GitHub account gives you all AI models** - This is incorrect
✅ **Student account gives you GitHub Copilot (OpenAI models only)**

### Available Claude Models (as of March 2026)

When you do get access to Claude, here are the current models:
- **Claude Opus 4.5** - Most capable model
- **Claude Sonnet 4.5** - Balanced performance and speed
- **Claude Haiku 4** - Fastest, most cost-effective

Note: Claude 4.6 Sonnet mentioned in your query may not exist yet. The latest Sonnet version is likely 4.5.

### Next Steps

1. **Clarify which service you want:**
   - Continue with GitHub Copilot (OpenAI models)
   - Switch to Claude (requires Anthropic access)

2. **Get appropriate access:**
   - For Claude: Sign up at console.anthropic.com
   - For Copilot: You already have this through your student account

3. **Install correct VS Code extension:**
   - For GitHub Copilot: GitHub Copilot extension
   - For Claude: Extensions like "Claude Dev", "Continue", or other Anthropic-compatible extensions

### Resources

- Anthropic Console: https://console.anthropic.com/
- Claude AI: https://claude.ai/
- GitHub Copilot: https://github.com/features/copilot
- VS Code Marketplace: https://marketplace.visualstudio.com/vscode

### Still Need Help?

If you're still experiencing issues:
1. Specify which VS Code extension you're using
2. Share the exact error message
3. Confirm whether you have Anthropic API access
4. Check if your organization has enterprise agreements with Anthropic
