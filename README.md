# Jepela

Jepela is a decision API with memory: send a state and typed questions (choice, score, yes/no), get typed answers
with a probability for every option in one call. Name a subject, and Jepela also uses what that subject's memory
holds, and shows you what it changed.

Jepela is a hosted API at `https://api.jepela.com`. This repository holds the public client code:

| Folder | What it is |
|---|---|
| `sdk/python` | Python client, standard library only |
| `sdk/typescript` | TypeScript client, no dependencies |
| `plugins/jepela` | MCP server and Claude Code plugin |
| `skills/jepela` | An agent skill: when and how to use Jepela in the software an agent writes |
| `cookbooks` | Runnable recipes against the API |

Documentation: https://jepela.com/docs/index.html · Live demos: https://demo.jepela.com

## A key

Create an account at [app.jepela.com](https://app.jepela.com/#register) and choose your region. Jepela approves new
accounts; then you create your key in the console and add credit by card or by invoice. Questions:
[info@jepela.com](mailto:info@jepela.com).

## One request

```bash
export JEPELA_API_KEY=jj_live_...
curl -s https://api.jepela.com/v1/systemone \
  -H "Authorization: Bearer $JEPELA_API_KEY" -H "Content-Type: application/json" \
  -d '{"state": "You charged me twice for September. Please send the second payment back.",
       "questions": {"refund": {"type": "noul", "instructions": "Is the customer asking for money back?"}}}'
```

## Python

```bash
pip install "git+https://github.com/jepelasweden/jepela#subdirectory=sdk/python"
```

## Claude Code

```
/plugin marketplace add jepelasweden/jepela
/plugin install jepela@jepela
```
