# research-skills

A small collection of research and academic-workflow skills for Claude — use them
on the web (claude.ai), in the desktop app, or in Claude Code.

> ⚠️ **For testing purposes only.** The skills here are works-in-progress
> published for evaluation. They are not validated or supported for production or
> real research use — verify everything at the source before relying on it.

## Skills

### `literature-search-pipeline`

A simple, human-in-the-loop workflow for searching academic literature across
every connected source at once, with **one review gate**: you approve the Boolean
search before anything runs. In short, the pipeline:

1. **Clarifies scope** — only if your question is ambiguous, asks short
   multiple-choice questions (date range, population, study types, etc.).
2. **Builds** a Boolean search — synonyms, variant spellings, related terms, plus
   an optional MeSH variant for health topics — and waits for your approval.
3. **Searches** every available source simultaneously, deduplicates, and returns a
   themed reference list with a short summary of each article.
4. **Offers next steps** as a multiple-choice question:
   - **Citation chaining** — backward and forward from seed papers you confirm.
   - **RIS export** — a file of full records (including abstracts) to import into
     Zotero via *File → Import*.

Throughout, it **verifies before trusting** — it only reports records a real tool
call returned — and **every record includes a working hyperlink to its source.**

## Installing

Most people use Claude on the **web (claude.ai)** or the **desktop app** — start
there. Claude Code users can add the marketplace instead.

### Claude Desktop & web (claude.ai)

The desktop app and claude.ai share the same Skills settings. They don't use the
plugin marketplace — you upload the skill as a ZIP.

1. **Turn on code execution.** Go to **Settings → Capabilities** and enable
   **"Code execution and file creation"** (Skills require it). Custom-skill upload
   is available on **Pro, Max, Team, and Enterprise** plans.
2. **Get the skill ZIP.** Download
   [`literature-search-pipeline.zip`](https://github.com/dastorie/research-skills/raw/main/literature-search-pipeline.zip)
   from this repo. *(It's already packaged correctly — the ZIP contains a
   `literature-search-pipeline/` folder with `SKILL.md` inside. If you build your
   own, keep that structure: the skill folder must be at the root of the ZIP, not
   the loose files.)*
3. **Upload it.** Open **[Customize → Skills](https://claude.ai/customize/skills)**,
   click **+ Create skill** (the **+** button), and upload the ZIP. Uploaded
   skills are private to your account and appear under Customize → Skills, where
   you can toggle or delete them.
4. **Use it.** Just ask a research question (e.g. *"find the literature on X"*) —
   with the skill enabled, Claude invokes it automatically.

> Team/Enterprise: an owner can also publish it org-wide from
> **Organization settings → Skills**.

### Claude Code (CLI)

```
/plugin marketplace add dastorie/research-skills
/plugin install literature-search-pipeline@research-skills
```

Then ask a research question (e.g. *"find the literature on X"*) and the skill
triggers automatically.

## Connected sources

The pipeline orchestrates external academic MCP servers. For full functionality
you need some of these connected in your Claude environment:

- **Consensus** — natural-language search over peer-reviewed papers.
- **OpenAlex** — structured metadata, citation graphs, trends, author disambiguation.
- **academic-search** — regex queries and citation walks (PubMed / OpenAlex /
  Semantic Scholar providers).

OpenAlex is also the source of the full records used for the RIS export. No
Zotero connector is needed — the RIS file imports directly.

If a source isn't connected, the skill says so and continues with the rest.

## License

Provided as-is, with no warranty, for testing and evaluation only.
