## 🤖 Bankerbot - Chatbot with Amazon Lex 

Let’s set up your very own chatbot in just one hour!

---

### 🧰 What You’ll Need
- An AWS account (create one [here](https://portal.aws.amazon.com/billing/signup))
- No coding experience necessary

---

### ⚡️ What You'll Learn
- How to build a chatbot using Amazon Lex
- How to define intents and responses
- How to use slots to collect user data
- How to connect Lex with AWS Lambda
- How to use context carryover across intents
- How to transfer money between accounts
- How to use confirmation prompts
- How to deploy with CloudFormation
---

## 🛠 Step 1: Set Up Your Lex Chatbot

1. Log in to the AWS Console
2. Navigate to **Amazon Lex** (search "Lex" in the AWS search bar)
3. Make sure you're in **Lex V2** (if not, switch using the left menu)
4. Click **Create bot** > **Create a blank bot** (you might need to switch to the *Traditional* tab)

### Bot Details
- **Bot name:** `BankerBot`
- **Description:** Banker Bot to help customers check their balance and make transfers
- **IAM Permissions:** Create a role with basic Amazon Lex permissions
- **COPPA:** No
- **Idle session timeout:** 5 minutes
- **Language:** English (US)
- **Voice:** Choose your favorite (Gregory and Ruth are great options!)
- **Intent confidence threshold:** 0.40

Click **Done** to create your bot.

---

## 💬 Step 2: Create the `WelcomeIntent`

This is the first intent to greet users.

### Intent Details
- **Intent name:** `WelcomeIntent`
- **Description:** Welcoming a user when they say hello

### Sample Utterances
```
Hi
Hello
I need help
Can you help me?
```

### Closing Response
```
Hi! I'm BB, the Banking Bot. How can I help you today?
```

Save the intent and **Build** the bot.

### Test
Open the test window and try:
- `Hi`
- `Help me`
- `Good morning` (this one will likely trigger fallback)

---

## 🚧 Step 3: Manage FallbackIntent

FallbackIntent is triggered when the chatbot cannot recognize the user’s input.

### Custom Response
**Message:**
```
Sorry I am having trouble understanding. Can you describe what you'd like to do in a few words? I can help you find your account balance, transfer funds and make a payment.
```

**Variation:**
```
Hmm could you try rephrasing that? I can help you find your account balance, transfer funds and make a payment.
```

Save and **Build** again.

---

## 🌟 Create a Custom Slot for Account Types

Now let’s create a slot for account types.

1. Go to **Slot types** from the left panel
2. Click **Add slot type** > **Add blank slot type**
3. Name it: `accountType`
4. Under **Slot value resolution**, choose **Restrict to slot values**

### Values
| Value    | Synonyms                                    |
|----------|---------------------------------------------|
| Checking | -                                           |
| Savings  | -                                           |
| Credit   | credit card; visa; mastercard; amex; american express |

✅ Save the slot type

---

## 💰 Step 4: Create the `CheckBalance` Intent

This intent helps the user check their bank balance.

1. Go to **Intents** > **Add intent** > **Add empty intent**
2. Name it: `CheckBalance`
3. Description: `Intent to check the balance in the specified account type`

### Sample Utterances
```
What’s the balance in my account?
Check my account balance
What’s the balance in my {accountType} account?
How much do I have in {accountType}?
I want to check the balance
Can you help me with account balance?
Balance in {accountType}
```

### Add Slots
1. **Slot Name:** `accountType`
   - Slot Type: `accountType`
   - Prompt: `For which account would you like your balance?`

2. **Slot Name:** `dateOfBirth`
   - Slot Type: `AMAZON.Date`
   - Prompt: `For verification purposes, what is your date of birth?`

✅ Save and **Build** the bot

---

## 🧪 Step 5: Test Your Bot

Open the test window and try:
- `I want to check my balance please`
- Respond with your account type and birth date

You’ll see the message:
> `Intent CheckBalance is fulfilled`

Click **Inspect** to confirm that both slots are correctly filled.

Try another message:
> `What’s the balance in my savings account?`

This time, only your date of birth will be requested because the `accountType` is detected from the utterance.

---
## 🧠 Step 6: Create Your AWS Lambda Function

Now that BankerBot can collect user details, let’s give back a fake bank balance!

1. Go to **AWS Lambda** in the AWS Console
2. Click **Author from scratch**
3. **Function name:** `BankingBotEnglish`
4. **Runtime:** Python 3.12
5. Click **Create function**
6. In the **Function code** section, open `lambda_function.py`
7. Paste in your Python code to generate a random bank balance
8. Click **Deploy**

---

## 🔗 Step 7: Connect Lambda with Lex

Now link your Lambda function with your chatbot:

1. Go to **Lex > BankerBot > Aliases**
2. Choose **TestBotAlias**
3. Select **English (US)** in Languages panel
4. In the Lambda panel:
   - **Source:** BankingBotEnglish
   - **Version:** $LATEST
5. Click **Save**

---

## 🤝 Step 8: Connect Lambda to `CheckBalance` Intent

1. Navigate to **Intents > CheckBalance**
2. Scroll to **Fulfillment**
3. Expand **On successful fulfillment** > **Advanced options**
4. Check **Use a Lambda function for fulfillment**
5. Click **Update options**
6. Click **Save intent** and **Build** the bot again

## 💾 Step 9: Enable Context Carryover

### Part A: Create Output Context in `CheckBalance`

1. Go to **CheckBalance** intent
2. Scroll to **Contexts** section
3. Under **Output contexts**, add new tag: `contextCheckBalance`
4. Set timeout to `5 turns` or `90 seconds`
5. Save intent and **Build**

### Part B: Create `FollowupCheckBalance` Intent

1. Add a new intent: `FollowupCheckBalance`
2. Description: Intent to allow a follow-up balance check request without authentication
3. Input context: `contextCheckBalance`
4. Sample utterances:
```
How about my {accountType} account?
What about {accountType}?
And in {accountType}?
```

### Add Slots
1. **Slot Name:** `accountType`
   - Slot Type: `accountType`
   - Prompt: `For which account would you like your balance?`

2. **Slot Name:** `dateOfBirth`
   - Slot Type: `AMAZON.Date`
   - Prompt: `For verification purposes, what is your date of birth?`
   - Default value: `#contextCheckBalance.dateOfBirth`

### Fulfillment Setup
- Scroll to **Fulfillment**
- Enable Lambda function for fulfillment (same one as CheckBalance)
- Save and **Build**

### Test Flow
1. First trigger `CheckBalance` to set the context
2. Then test `FollowupCheckBalance` using utterance like:
   - `How about my credit account?`
   - It should skip asking for date of birth again

---

🎉 Great job! You’ve just enabled your chatbot to remember user info across intents!


Test again:
- `What’s the balance in my savings account?`

The chatbot should now respond with a random balance!

---

🎉 Amazing work! You’ve:
- Connected Lex with Lambda
- Enabled your chatbot to return dynamic data


## 🔄 Step 10: Create the `TransferFunds` Intent

Create a new intent to allow users to transfer money between accounts.

### Intent Details
- **Name:** `TransferFunds`
- **Description:** Help user transfer funds between bank accounts

### Sample Utterances
```
Can I make a transfer?
I want to transfer funds
I'd like to transfer {transferAmount} from {sourceAccountType} to {targetAccountType}
Can I transfer {transferAmount} to my {targetAccountType}?
Would you be able to help me with a transfer?
Need to make a transfer
```

### Slots
| Slot Name           | Slot Type     | Prompt                                      |
|--------------------|---------------|---------------------------------------------|
| sourceAccountType  | accountType   | Which account would you like to transfer from? |
| targetAccountType  | accountType   | Which account are you transferring to?        |
| transferAmount     | AMAZON.Number | How much money would you like to transfer?    |

### Confirmation Prompt
- **Prompt:** `Got it. So we are transferring {transferAmount} from {sourceAccountType} to {targetAccountType}. Can I go ahead with the transfer?`
- **Decline Response:** `The transfer has been cancelled.`

### Closing Response
```
The transfer is complete. {transferAmount} should now be available in your {targetAccountType} account.
```

✅ Save and **Build** the bot

---

## 🖼 Step 11: Explore Lex Visual Tools

### Conversation Flow
- Navigate to the top of the intent setup page
- Expand **Conversation flow**
- Visualize how Lex handles the entire dialog

### Visual Builder
- Use the **Visual builder** button at the bottom of the page
- Drag and drop to build or update your intent visually

---

## ☁️ Step 12: Deploy with CloudFormation

Instead of manually rebuilding your bot every time:

1. Open **CloudFormation** in the AWS Console
2. Choose **Create stack** > **Upload a template file**
3. Upload the `nextwork-banker-bot.yaml` file
4. Name your stack: `nextwork-banker-bot-name`
5. Follow through the steps and check **Capabilities** boxes
6. Submit and wait for `CREATE_COMPLETE` status

### Troubleshooting Tip
If the bot returns `Intent CheckBalance is fulfilled` without real output:
- Recreate Lambda with correct permissions
- Add resource-based policy to allow Lex alias to invoke it

---

## 🧹 Cleanup Resources

1. Delete your **Lex Bot** (BankerBot)
2. Delete your **Lambda function**
3. Delete **CloudWatch logs** (via Log Groups)
4. If deployed via **CloudFormation**, delete the stack to remove all associated resources

---

🎉 **Congratulations!**

You’ve now built a complete banking chatbot with:
- ✅ Intents and slots
- ✅ Lambda integration
- ✅ Context carryover
- ✅ Multi-slot handling
- ✅ Confirmation prompts
- ✅ Visual tools
- ✅ CloudFormation automation

You’re officially a Lex Bot Builder. 🏆
