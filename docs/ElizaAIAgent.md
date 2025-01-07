### Eliza AI Agent + X (Twitter)

#### Step 1: install NodeJS v22+
[https://nodejs.org/en/download](https://nodejs.org/en/download)

#### Step 2: install pnpm (package manager)
[https://pnpm.io/installation](https://pnpm.io/installation)

```
curl -fsSL https://get.pnpm.io/install.sh | sh -
```

#### Step 3: create X account and generate OpenAI API key

3.1. Create account on X (Twitter). In the next steps, we will need username, password and email.

3.2. Generate OpenAI API Key and refill with some credits amount ($5): [https://platform.openai.com/api-keys](https://platform.openai.com/api-keys)

3.3. Generate OpenRouter AI API key and refill with some credits amount ($5): [https://openrouter.ai/settings/keys](https://openrouter.ai/settings/keys)

#### Step 4: clone eliza-started repo
```
git clone https://github.com/elizaOS/eliza-starter.git
```

#### Step 5: configure Eliza

5.1. Open terminal and navigate to cloned `eliza-starter` directory:
```
cd eliza-starter
```

5.2. Create new file `.env` in root directory and copy content from `.env.example`:
```
cp .env.example .env
```

5.3: Update environment variables using keys created on Step 3:
```
OPENAI_API_KEY=sk-proj-...
OPENROUTER_API_KEY=sk-or-v1-...
TWITTER_USERNAME=<username>
TWITTER_PASSWORD=<password>
TWITTER_EMAIL=<email>
POST_INTERVAL_MIN=1
POST_INTERVAL_MAX=3
```

Leave the other parameters untouched

5.4 open `package.json` and update better-sqlite3 version to 11.7.0:
```
    "better-sqlite3": "11.7.0",
```

5.5. Install dependencies

Run in the root directory
```
pnpm install
```

### Step 6: configure Eliza characted

6.1 Open file `characters/eliza.character.json`

6.2 Modify Line 3: add Twitter client:
```
  "clients": ["twitter"],
```

Optional: adjust some params in `characters/eliza.character.json`: bio, lore, messageExamples, etc.

### Step 7: run Eliza X (Twitter) AI agent

```
pnpm start --characters="characters/eliza.character.json"
```

If everything is configured correctly, you should see message ` ["◎ Next tweet scheduled in N minutes"]`.

<img width="499" alt="Screenshot 2025-01-07 at 2 08 37 PM" src="https://github.com/user-attachments/assets/681b354a-8a46-4407-a087-4ede21a6bccb" />


