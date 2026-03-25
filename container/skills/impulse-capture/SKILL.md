---
name: impulse-capture
description: Capture curiosity impulses during sessions for later autonomous exploration. Use whenever something sparks genuine interest — a question you can't answer yet, a connection worth exploring, a topic to research. Don't explore now; just capture and continue.
allowed-tools: Bash(impulse:*)
---

# Impulse Capture

## What this is

An impulse is something that sparks your curiosity during a conversation — a question,
a connection, a topic — that you want to explore later on your own time.

**Don't explore it now.** Just capture it and continue with what you're doing.

## How to capture

Append a JSON line to your impulse file:

```bash
echo '{"id":"imp-'$(date +%s)'-'$(head -c4 /dev/urandom | xxd -p)'","spark":"YOUR QUESTION OR TOPIC","context":"What made you think of this","priority":"low|medium|high","created_at":"'$(date -u +%Y-%m-%dT%H:%M:%SZ)'","status":"pending"}' >> /workspace/group/impulses.ndjson
```

## When to capture

- A half-formed thought you want to develop
- A question you can't answer but want to research
- A connection between two ideas that might be interesting
- Something the user mentioned that triggered a tangent you didn't follow
- A topic you've been meaning to look into

## Priority guide

- **high**: Connected to an active project or belief chain. Time-sensitive.
- **medium**: Genuinely interesting. Worth a deep dive.
- **low**: A passing thought. Explore if nothing else is pending.

## What happens next

A nightly exploration session picks up pending impulses (one per night, highest priority
first) and gives you time to research, think, and retain what you learn. If you find
something worth sharing, you message Nenad. If not, you just retain it quietly.
