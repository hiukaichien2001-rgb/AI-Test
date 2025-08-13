```markdown
## Bug #1: [".env file not loaded"]

**Error/Issue Observed:**
[GOOGLE_API_KEY was always empty even when .env existed.]

**LLM Assistance Used:**
[It suggested calling load_dotenv() before os.getenv.]

**Root Cause:**
[load_dotenv() was imported but never called]

**Fix Applied:**
[Called load_dotenv() at the start of demo.py.]


**Verification:**
[Created .env with GOOGLE_API_KEY=.... The app switched from mock mode to real mode.]
```

```markdown
## Bug #2: ["Missing `run_mock_demo()"]

**Error/Issue Observed:**
[When no key was set, the app called run_mock_demo() and crashed.]

**LLM Assistance Used:**
[It suggested a mock function returning safe canned outputs]

**Root Cause:**
[run_mock_demo() was never implemented]

**Fix Applied:**
[Implemented run_mock_demo() with simple mock responses]


**Verification:**
[Unset the key and ran the app. It no longer crashed and printed mock results.]

```markdown
## Bug #3: ["Tools not fully initialized and not passed to router"]

**Error/Issue Observed:**
[Weather and calculator queries did nothing useful. Only news tool existed.]

**LLM Assistance Used:**
[It suggests instantiate all tools and pass them to the router.]

**Root Cause:**
[Only FakeNewsSearchTool() was created, and ConversationRouter received no tools.]

**Fix Applied:**
[Instantiate all three tools and pass them into ConversationRouter.]


**Verification:**
[Weather, calculator, and news queries now produce tool outputs in real mode.]