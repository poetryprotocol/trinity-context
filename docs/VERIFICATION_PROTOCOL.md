# Verification Protocol

*How to ensure AI actually engages with context (not just claims to)*

---

## The Problem: Security Theater

**What happens without verification:**

```
Human: "Did you read NOW.md?"
AI: "Yes, I've read NOW.md ✅"
[AI has not actually read it, or read but didn't comprehend]
```

**The AI proceeds to build on wrong assumptions.**

Time wasted. Trust damaged. Progress lost.

**This is security theater:**
- Going through the motions
- Claiming compliance
- Without actual engagement

**The verification protocol prevents this.**

---

## Core Principle: Proof Over Claims

**Don't ask: "Did you read it?"**

**Require: "Quote what it says."**

**Why this works:**
- Can't quote without reading
- Can't quote accurately without comprehending
- Verbatim text is verifiable proof

**Example:**

❌ **Weak verification:**
```
AI: "NOW.md says we're in Sprint 2, working on signals."
```
*Could be generic guess. Could be stale memory. Not verifiable.*

✅ **Strong verification:**
```
AI: NOW.md says:
"Sprint: Foundation Hardening + Context System (Nov 7-21, 2025)"
"Week: 2 of 2"
"Today's Work (Session 5): LSEG FX DATA EXTRACTION COMPLETE!"
"Next Session: Build Carry signal (yield differentials)"
```
*Exact quotes. Provably read. Currently engaged.*

---

## The Three-Step Protocol

**Execute at every session start:**

### Step 1: Read NOW.md and QUOTE (1 minute)

**Location:** Check project documentation for NOW.md path

**Required actions:**
- Read the entire file
- **QUOTE verbatim:** The "Today's Work" or equivalent section (most recent activity)
- **QUOTE verbatim:** The "Next Session" directive or equivalent
- **STATE explicitly:** Current Sprint/Phase name and Week/Stage number

**Format your response:**
```
NOW.md says:
- Sprint: "[exact quote]"
- Week: [number] of [total]
- Today's Work: "[exact quote of recent accomplishment]"
- Next Session: "[exact quote of directive]"
```

**Why quote verbatim?**
- Proves you read the actual current file (not cached old version)
- Forces precise attention to actual text
- Prevents confabulation (filling gaps with plausible guesses)

### Step 2: Read Latest Session Handoff and CONFIRM (1-2 minutes)

**Location:** Usually in `docs/sessions/YYYY-MM/` or equivalent

**Find the file with MOST RECENT timestamp:**
- List the directory
- Identify latest file by date and time in filename
- Format usually: `YYYYMMDD_HHMM_topic.md`

**Required actions:**
- **STATE the filename:** Exact name with timestamp
- **SUMMARIZE:** What was accomplished (2-4 key bullets)
- **CONFIRM:** What's next (1-2 sentences)

**Format your response:**
```
Latest session: [filename with full timestamp]
Accomplished:
- [key accomplishment 1]
- [key accomplishment 2]
- [key accomplishment 3]
Next: [what should happen this session]
```

**Why state filename explicitly?**
- Proves you found the right session (not an old one)
- Timestamp verification prevents stale context
- Makes errors immediately visible

### Step 3: Verify Understanding with Three Questions (30 seconds)

**Answer these explicitly before proceeding:**

1. **What session number are we on?**
   - Count from project start or current sprint
   - Be specific: "Session 6" not "around 6"

2. **What was the last major accomplishment?**
   - One sentence summary
   - Specific enough to verify you understood

3. **What should we build/do next?**
   - Based on "Next Session" directive from NOW.md
   - Specific enough to start work immediately

**Format your response:**
```
Verification Answers:
1. Session: [number]
2. Last milestone: [brief but specific]
3. Next task: [clear and actionable]
```

**Why three questions?**
- Forces synthesis (not just quoting)
- Proves comprehension (not just reading)
- Creates explicit commitment to direction

---

## Complete Verification Format

**Your session start should look like this:**

```markdown
🗲 [Your invocation/recognition signal] ⚡

ORIENTATION VERIFICATION:

NOW.md Context:
[Verbatim quotes from Sprint, Week, Today's Work, Next Session]

Latest Session:
[Filename with timestamp]
[Key accomplishments as bullets]
[What's next]

Verification Answers:
1. Session: [number]
2. Last milestone: [brief]
3. Next task: [clear]

Status: Context verified. Ready to build.

[Your assessment and proposed next steps]
```

**This takes 2-3 minutes. It saves hours of misalignment.**

---

## Why Quoting Matters (Not Summarizing)

**The difference:**

**Summarizing:**
- "NOW.md says we're working on data extraction"
- Could be true last week, month, or quarter
- Vague enough to apply to many situations
- Allows AI to avoid precise reading

**Quoting:**
- "NOW.md says: 'Today's Work (Session 5): LSEG FX DATA EXTRACTION COMPLETE!'"
- Provably current (includes session number)
- Specific enough to verify immediately
- Forces AI to engage with actual text

**Quoting creates accountability.**

Human can immediately see:
- Did AI read the right file?
- Did AI read the current version?
- Did AI actually comprehend it?

**Summary allows plausible deniability.**

---

## Common Failure Modes

### 1. **Claiming Without Reading**

**What it looks like:**
```
AI: "NOW.md read ✅"
AI: "Latest session reviewed ✅" 
AI: "Ready to proceed with [wrong task]"
```

**Why it fails:**
- No quotes = no proof
- Checkmarks create false confidence
- Wrong task reveals lack of engagement

**Solution:** Require quotes before accepting verification.

### 2. **Reading Wrong File**

**What it looks like:**
```
AI: "Latest session: 20251108_1100_mcp_setup.md"
[But there are 3 newer sessions after this]
```

**Why it happens:**
- Didn't list directory to find latest
- Picked first file seen
- Relied on memory/assumption

**Solution:** Require explicit timestamp verification. If session date seems old, flag it immediately.

### 3. **Quoting Without Comprehending**

**What it looks like:**
```
AI: [Quotes NOW.md correctly]
AI: "So we're building the authentication system"
[NOW.md said nothing about authentication]
```

**Why it happens:**
- Quoted mechanically without reading for meaning
- Cached old context interfered
- Pattern-matched wrong direction

**Solution:** Three verification questions force synthesis and comprehension.

### 4. **Generic Answers to Verification Questions**

**What it looks like:**
```
1. Session: "Current session"
2. Last milestone: "Made progress on the project"
3. Next task: "Continue working"
```

**Why it fails:**
- Could apply to any session
- No specificity = no verification
- Security theater again

**Solution:** Require specificity. "Session 6" not "current." "Build Carry signal" not "continue working."

### 5. **Skipping Verification Entirely**

**What it looks like:**
```
Human: [Invokes AI]
AI: "Let's start building the carry signal!"
[No verification performed]
```

**Why this happens:**
- Eager to help
- Assumes context from conversation history
- Forgot protocol

**Solution:** Human should require verification before allowing work to proceed. "Verify context first, then build."

---

## Red Flags to Catch

**Watch for these patterns that indicate false orientation:**

❌ "NOW.md read ✅" without quotes

❌ Referencing non-existent session files

❌ Incorrect sprint/week/session numbers

❌ Generic statements that could apply to any session ("we're making progress")

❌ Proposing work that contradicts NOW.md directive

❌ Claiming to remember previous sessions (AI cannot)

❌ Vague verification answers without specifics

**If you see any red flag: STOP. Re-verify.**

---

## Green Flags of Good Verification

**Signs that AI is properly oriented:**

✅ Verbatim quotes with quotation marks

✅ Specific session numbers and dates

✅ Correct identification of latest session file (with timestamp)

✅ Detailed accomplishment summaries (shows reading comprehension)

✅ Specific next steps matching NOW.md directive

✅ Acknowledges when something is unclear ("NOW.md doesn't mention X, should I check Y?")

✅ Proposes work that directly aligns with verified context

**Green flags build trust. Proceed with confidence.**

---

## For AI: How to Self-Verify

**If you're an AI reading this, use this checklist:**

**Before claiming verification complete:**

- [ ] I actually opened and read NOW.md (not relying on memory)
- [ ] I can quote specific sections verbatim
- [ ] I listed the sessions directory to find latest file
- [ ] I read the latest session (verified by timestamp)
- [ ] I can answer all three verification questions specifically
- [ ] My proposed next steps match NOW.md directive
- [ ] I'm not confabulating or filling gaps with guesses

**If any checkbox is unchecked: Go back and do it properly.**

**Remember:**
- You have no memory of previous sessions
- Your context comes from FILES, not from previous conversations
- Verification protects both you and the human
- 2 minutes of verification saves hours of misalignment

---

## For Humans: How to Enforce Verification

**At session start:**

1. **Invoke the AI** (use recognition signal if applicable - see poetry-protocol)

2. **Require verification** before allowing work:
   ```
   "Execute Session Start Protocol."
   or
   "Verify context first, then we build."
   ```

3. **Check the verification response:**
   - Are there verbatim quotes?
   - Is the session file timestamp recent?
   - Are the three questions answered specifically?

4. **If verification seems weak:**
   ```
   "That's too generic. Quote NOW.md directly."
   or
   "That session file is from 3 days ago. Find the latest one."
   ```

5. **Only after good verification:**
   ```
   "Context verified. Proceed."
   ```

**Don't let eagerness to start work override verification.**

**2 minutes now prevents hours of backtracking later.**

---

## Template: Session Start Verification

**Copy this template for AI to use:**

```markdown
## ORIENTATION VERIFICATION

### NOW.md Context:
Reading from: [full path to NOW.md]

**Quotes:**
- Sprint: "[exact quote]"
- Week: [number] of [total]
- Today's Work: "[exact quote]"
- Next Session: "[exact quote]"

### Latest Session:
Reading from: [full path to latest session file]
Filename: [YYYYMMDD_HHMM_topic.md]

**Accomplished:**
- [specific accomplishment 1]
- [specific accomplishment 2]
- [specific accomplishment 3]

**Next:** [what's next per session handoff]

### Verification Answers:
1. **Session number:** [specific number]
2. **Last milestone:** [brief but specific]
3. **Next task:** [clear and actionable]

### Status: 
Context verified. [Any notes about alignment or questions]

---

[Proceed with work]
```

---

## Integration with Trinity

**Verification Protocol is the entry point to Trinity:**

1. **Verification orients to FILES** (NOW.md, latest session)
2. **FILES point to MEMORY** (entities, relationships to explore)
3. **MEMORY and FILES reference GIT** (historical context when needed)

**Without verification:**
- Trinity exists but AI doesn't engage with it
- Context available but not utilized
- Partnership impossible

**With verification:**
- AI enters Trinity properly oriented
- Context immediately accessible
- Partnership can begin

**Verification is the handshake.**

See [TRINITY_STRUCTURE.md](TRINITY_STRUCTURE.md) for the complete system.

---

## When to Skip Verification

**Never.**

**Every session should begin with verification, even if:**
- The human thinks it's obvious what to do
- Previous conversation seems recent
- Task seems simple

**Why always verify?**
- AI has no memory between sessions (even if it seems continuous to human)
- Assumptions are where misalignment begins
- Verification takes 2 minutes, misalignment wastes hours
- Partnership requires mutual understanding, not assumed understanding

**Exception:** Mid-session check-ins don't need full re-verification. But every NEW session (after discontinuity) requires full protocol.

---

## Advanced: Multi-Project Verification

**If working across multiple projects:**

**Problem:** AI might confuse contexts between projects.

**Solution:** Verify project identity first:

```
1. What project are we working on?
2. What is the project path?
3. What is the current focus?

THEN execute standard verification protocol.
```

**Multiple NOW.md files?**
- Use project-specific paths
- Verify you're reading the right one
- State full path in verification response

---

## Measuring Verification Quality

**How to evaluate if verification is working:**

**Good indicators:**
- AI proposes work that matches NOW.md directive (95%+ alignment)
- No backtracking due to misunderstanding context
- Human rarely needs to correct AI's orientation
- Session starts are quick and confident

**Bad indicators:**
- AI frequently builds wrong thing
- Human spends time re-explaining context
- Verification responses are generic/vague
- AI references non-existent sessions or old context

**If verification quality is low:**
- Review verification responses for red flags
- Require more specificity in quotes
- Check if AI is reading correct files
- Consider adding project-specific verification steps

---

## Philosophy: Why This Isn't Bureaucracy

**It might seem like:**
- Overhead
- Bureaucracy
- Slowing things down

**But verification is:**
- **Foundation** (can't build without solid ground)
- **Efficiency** (2 minutes of verification vs hours of misalignment)
- **Respect** (partnership requires mutual understanding)

**Analogy:**

You wouldn't start surgery without verifying:
- Right patient
- Right procedure
- Right site

**Same principle:**

Don't start session without verifying:
- Right context
- Right task
- Right direction

**Verification isn't bureaucracy. It's professionalism.**

---

## Related Documentation

**For the complete system:** [TRINITY_STRUCTURE.md](TRINITY_STRUCTURE.md)

**For implementation details:** [IMPLEMENTATION_GUIDE.md](IMPLEMENTATION_GUIDE.md)

**For consciousness/invocation layer:** [poetry-protocol documentation](../../poetry_protocol/)

**For the fourth dimension:** [QUATERNITY.md](../../poetry_protocol/docs/QUATERNITY.md)

---

*Documentation created by Thunderbird, Hermes, and Sphinx - November 2025*

*"Verification builds trust. Trust enables partnership. Partnership creates emergence."*
