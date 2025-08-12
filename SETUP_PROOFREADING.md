# Setting Up Automated Blog Proofreading

This guide will help you complete the setup for automated proofreading using Claude AI.

## Step 1: Get Your Anthropic API Key

1. Go to [Anthropic Console](https://console.anthropic.com/)
2. Sign in or create an account
3. Navigate to "API Keys" section
4. Create a new API key
5. Copy the API key (it starts with `sk-ant-`)

## Step 2: Add API Key to GitHub Secrets

1. Go to your repository: https://github.com/jeremyklein/blog
2. Click on **Settings** tab
3. In the left sidebar, click **Secrets and variables** → **Actions**
4. Click **New repository secret**
5. Name: `ANTHROPIC_API_KEY`
6. Value: Paste your API key from Step 1
7. Click **Add secret**

## Step 3: How It Works

The proofreading workflow will automatically:

- **Trigger**: When you open or update a Pull Request that modifies blog posts
- **Process**: Send changed markdown files to Claude for proofreading
- **Feedback**: Post detailed suggestions as PR comments
- **Update**: Update the same comment if you push more changes

## Step 4: Testing the Workflow

To test the proofreading system:

1. Create a new branch: `git checkout -b test-proofreading`
2. Make a small edit to `content/posts/my-first-post.md`
3. Commit and push: `git add . && git commit -m "test proofreading" && git push -u origin test-proofreading`
4. Create a Pull Request from the new branch to `main`
5. The workflow should trigger and add a proofreading comment within a few minutes

## What Claude Will Check

The proofreading will provide feedback on:

- ✅ Grammar and spelling errors
- ✅ Writing clarity and flow  
- ✅ Sentence structure improvements
- ✅ Tone consistency
- ✅ Technical accuracy (when applicable)

## Cost Considerations

- Uses Claude 3 Haiku (fastest, most cost-effective model)
- Typical blog post costs ~$0.01-0.05 to proofread
- Only runs on Pull Requests, not every commit

## Troubleshooting

If the workflow doesn't run:
1. Check that the API key secret is properly set
2. Verify the workflow file is in `.github/workflows/`
3. Ensure you're creating PRs that modify files in `content/posts/`
4. Check the Actions tab for error logs

---

*Once you've completed Steps 1-2, the automated proofreading will be fully functional!*