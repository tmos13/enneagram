# Enneagram Assessment

**A TMOS13 pack for deep personality typing via the Enneagram.**

Nine types. Three centers. Wing identification. Growth and stress paths.
Slower and more reflective than MBTI — the Enneagram reaches underneath
behavior into motivation.

---

### The nine types

1 — The Reformer · 2 — The Helper · 3 — The Achiever
4 — The Individualist · 5 — The Investigator · 6 — The Loyalist
7 — The Enthusiast · 8 — The Challenger · 9 — The Peacemaker

### The deliverable

`enneagram_profile` — core type, wing, center, stress and growth arrows,
integration level, honest description of the type at its best and hardest.

---

### Pack structure

```
enneagram/
├── README.md
├── header.yaml
└── MANIFEST.md
```

---

### Run it yourself

This is a reference implementation of a TMOS13 pack. Clone the repo,
load the protocol into any Claude API session, and run it directly.

**Minimum setup:**

```python
import anthropic

with open("MANIFEST.md", "r") as f:
    manifest = f.read()

client = anthropic.Anthropic()

messages = []

print("Session started. Type your message.\n")

while True:
    user_input = input("You: ")
    messages.append({"role": "user", "content": user_input})

    response = client.messages.create(
        model="claude-opus-4-5-20251101",
        max_tokens=1024,
        system=manifest,
        messages=messages
    )

    reply = response.content[0].text
    messages.append({"role": "assistant", "content": reply})
    print(f"\nAssistant: {reply}\n")
```

Requires: `pip install anthropic` and an `ANTHROPIC_API_KEY` environment variable.

For the full TMOS13 engine — pack state management, vault, deliverables,
multi-cartridge routing — visit [tmos13.ai](https://tmos13.ai).

---

**TMOS13, LLC** · Deploy Yourself™
