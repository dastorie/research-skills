# research-skills

A small [Claude Code](https://claude.com/claude-code) plugin marketplace of
research and academic-workflow skills.

> ⚠️ **For testing purposes only.** The skills here are works-in-progress
> published for evaluation. They are not validated or supported for production or
> real research use — verify everything at the source before relying on it.

## Skills

### `literature-search-pipeline`

A guided, human-in-the-loop workflow for searching academic literature across
every connected source at once. It runs in distinct phases with **two mandatory
review gates** — you inspect and edit the concept blocks and the queries *before*
any searching happens. In short, the pipeline:

1. **Decomposes** your question into PICO / thematic concept blocks (review gate 1).
2. **Builds** Boolean queries — synonyms, variant spellings, related terms, and a
   MeSH controlled-vocabulary variant (review gate 2).
3. **Searches** every available source simultaneously and deduplicates results.
4. **Layers** the search iteratively with a reproducible audit log (PRISMA-friendly).
5. **Snowballs** citations backward and forward from the strongest seed papers.
6. **Verifies before trusting** — only reports records a real tool call returned,
   and **every record includes a working hyperlink to its source.**

## Installing

In Claude Code:

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
- **A library catalog MCP** — referenced in the skill as a generic `Library
  Catalog` placeholder; substitute whatever institutional catalog MCP you have
  connected (its real tool names will differ).
- **Zotero** *(optional)* — capture the final set at the end.

If a source isn't connected, the skill says so and continues with the rest.

## License

Provided as-is, with no warranty, for testing and evaluation only.
