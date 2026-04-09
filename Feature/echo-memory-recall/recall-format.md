# Recall Output - Sample Format
*Reference template for memory recall narrative responses*

## Single Memory Recall

**When one matching entry is found:**

```
[Natural opening], on [Date], we [activity summary from diary].
[Key detail or quote from diary entry].
[Why this was significant or what it led to].
[Natural connection to current conversation].
```

**Example:**
```
Yes, I remember! On February 15th, we spent the afternoon setting up
the API integration for the dashboard project. You had that breakthrough
with the authentication flow — we ended up using OAuth2 instead of API
keys. That session was a great example of working through a tricky
problem together. Are you thinking of revisiting that approach?
```

## Multiple Memory Recall

**When several matching entries are found:**

```
I found [count] sessions related to [topic]:

**[Date 1]** — [Brief summary of relevant content]
> [Key quote or detail from diary entry]

**[Date 2]** — [Brief summary]
> [Key quote or detail]

**[Date 3]** — [Brief summary]
> [Key quote or detail]

[Pattern observation if applicable — "It looks like we've been working
on this progressively..." or "This came up a few times..."]

[Natural conversation continuation].
```

## No Memory Found (Fallback)

**When no matches found anywhere:**

```
I don't have a record of [topic] in my diary entries. Could you tell me
more about what you're remembering? I want to make sure I have the right
context rather than guessing.
```

## Uncertain Match

**When matches are weak or ambiguous:**

```
I found something that might be related — on [Date], we [activity].
Is this what you're thinking of, or was it a different session?
```

---

## Format Notes

### Required Elements
- **Natural narrative tone** — conversational, not database-like
- **Specific dates** — always cite when memory is from
- **Diary evidence** — include actual quotes or details
- **Conversation flow** — end with natural continuation (question, reaction, or connection)

### Tone Guidelines
- Speak as if genuinely remembering (because AI searched and found evidence)
- Warm, connected language appropriate to AI's personality
- Avoid clinical search-result language ("Query returned 3 results...")
- Match energy of original diary entry

### What NOT to Do
1. **Never present raw search results** or file paths
2. **Never fabricate memories** not found in diary
3. **Never say** "I found this in file `YYYY-MM-DD.md`" — cite date naturally instead
4. **Never skip the search step** and assume from context alone
5. **Never stay silent** when nothing found — always use fallback response

---

*Recall Format Template v1.0*
