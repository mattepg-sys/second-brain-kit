# Pattern: contacts table + a few cards

**Fits when:** the person has many contacts (a community, a class, event attendees, a WhatsApp group), but only some need a full file. One Markdown file per person would be hundreds of files nobody reads.
**Default otherwise:** one file per person in `People/` (`_guide/templates/person.md`).

---

## Two levels

1. **A table for everyone:** `People/contacts.csv`, one row per person.
2. **A card for the people who matter:** `People/firstname-lastname.md` (template `person.md`) only for people with an ongoing relationship, open promises or a shared project. The table row links to the card.

Suggested columns (adapt):

```
name;organization;role;how we met;related to;email;phone;card;last contact;notes
```

## Practical details

- **Separator and encoding:** if the person will open the file in Excel, use `;` as the separator in countries where the comma is the decimal mark (most of Europe), and save as **UTF-8 with BOM** so accented names display correctly. Otherwise `,` and plain UTF-8 are fine.
- **Store only what the person wants stored.** Phone numbers and emails are personal data of other people: ask what they want kept.
- **Importing lists** (an Excel file from an event, a group export): put the originals in `People/to-import/`, import them with the person's OK (merge duplicates, keep the source in "notes"), then archive the originals. A one-off import doesn't need a flow.
- Flows that meet a new person add a row; they propose a card only when the person becomes important (a promise, a meeting, a project).
- Register both: `people` (the folder) and, if a flow writes to it, `contacts` (the CSV, kind `folder` or `destination`).
