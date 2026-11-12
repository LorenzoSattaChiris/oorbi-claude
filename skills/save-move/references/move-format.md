# A Move, written out

Synthetic example.

The person improved a prompt for a weekly client update and asks: "save this as a Move".

What you show before saving:

> **Weekly client update**
> A short weekly update for one client: progress, risks and next steps.
>
> Library: Personal. Only you can see it until you share it in Oorbital.
>
> ```text
> Write a weekly update for {{client}} covering this week's progress, open risks and next steps.
>
> Progress and notes:
> """
> {{notes}}
> """
>
> Keep it under {{words|200}} words, in a calm, factual tone. Start with the single most important point.
> ```
>
> It asks for:
> - `client`: Which client is this for? (for example, Northwind)
> - `notes`: What happened this week?
> - `words`: How many words at most? (default 200)
>
> Saving sends this title and instruction to Oorbital, where it is kept in your library. Save it?

After "yes", the `save_move` call carries exactly:

```json
{
  "workspaceId": "<the personal library's workspaceId from get_oorbi_context>",
  "title": "Weekly client update",
  "summary": "A short weekly update for one client: progress, risks and next steps.",
  "instruction": "Write a weekly update for {{client}} covering this week's progress, open risks and next steps.\n\nProgress and notes:\n\"\"\"\n{{notes}}\n\"\"\"\n\nKeep it under {{words|200}} words, in a calm, factual tone. Start with the single most important point.",
  "inputs": [
    { "key": "client", "question": "Which client is this for?", "example": "Northwind" },
    { "key": "notes", "question": "What happened this week?" },
    { "key": "words", "question": "How many words at most?" }
  ]
}
```

## Good inputs

- Use an input for what changes each time: a name, the material to work on, a date, a length.
- Keep fixed method words in the instruction: the structure, the tone, the checks.
- One input per idea. `{{client}}` and `{{notes}}`, not `{{everything}}`.
- A default (`{{words|200}}`) makes an input optional.
