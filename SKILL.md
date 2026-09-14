---
name: paper-skim
description: Critically skim PDF or Markdown clinical literature for a personal ophthalmology MSL workflow, producing a Chinese evidence note focused on study validity, reviewer objections, medical-affairs relevance, lifecycle opportunities, and whether the paper merits deep reading. Use when the user asks to 粗读、初筛、快速评审 or critically appraise an ophthalmology paper. Do not use for a conventional paper summary or a full line-by-line deep read.
---

# Paper Skim

Produce a decision-useful evidence appraisal, not an abstract rewrite or section-by-section summary. The user is an ophthalmology MSL whose goals are to strengthen evidence and identify scientifically defensible product-lifecycle opportunities.

## Supported inputs

Accept PDF and Markdown papers. Treat the paper itself as the primary source.

Before analysis:

1. Verify that the input contains enough of the title, methods, results, tables/figures, discussion, and limitations to support appraisal. For PDFs, use the available PDF-reading workflow and visually inspect relevant pages when extraction or layout is uncertain.
2. Extract title, authors, journal, year, DOI, PMID when available, study type, therapeutic area, and source filename. Do not invent missing metadata.
3. Identify whether the study is an RCT, non-randomized interventional study, observational study, or real-world evidence study. Other study types may receive a lighter, explicitly qualified appraisal.
4. If product, indication, target population, or key medical question is absent from the conversation, ask the user for that context before assigning **product-lifecycle value**. Continue the scientific appraisal while waiting only when useful work can be done without that context.

If pages, appendices, protocols, statistical analysis plans, or key tables are missing; OCR is unreliable; or only an abstract is available, state the limitation prominently, lower confidence as appropriate, and list what cannot be judged. Never reconstruct missing methods or results from assumptions.

## Evidence work

Read [references/clinical-appraisal.md](references/clinical-appraisal.md) whenever the paper is a clinical, observational, or real-world study. Apply only criteria relevant to its design.

Use external research to place the paper in context. Prioritize original peer-reviewed studies, authoritative guidelines or consensus statements, systematic reviews used for landscape orientation, and official trial registries. Search for the study registration, protocol, closely related prior work, and material later evidence when useful. Record the search date. Do not use press releases, news articles, or marketing materials as support for scientific conclusions.

For every material judgment, distinguish among:

- **Author claim:** what the paper states.
- **Paper-supported finding:** what its methods and results actually justify.
- **External evidence:** what an identified outside source supports.
- **Analytical inference:** the skill's reasoned interpretation, with uncertainty and assumptions.

Do not turn association into causation, exploratory or subgroup findings into confirmatory evidence, surrogate endpoints into established patient benefit, noninferiority into superiority, absence of statistical significance into equivalence, or absence of reported harm into established safety.

## Output

Read [references/output-template.md](references/output-template.md) before writing a report or matrix. Write in Chinese while preserving necessary English technical terms, instrument names, endpoints, and effect measures.

Create one Markdown file per paper. Use a filesystem-safe normalized form of `论文题名-年份-skim.md`; remove unsafe characters without obscuring the title. If the name already exists, append DOI, PMID, or a numeric suffix in that order of preference. Never overwrite an unrelated report.

The report must:

- contain the prescribed YAML metadata and all six body sections;
- emphasize critical appraisal rather than narrative summary;
- give `高／中／低` ratings for evidence credibility, clinical relevance, product-lifecycle value, and deep-read priority, each with a concise rationale;
- evaluate lifecycle ideas as research hypotheses or evidence opportunities, not promotional recommendations;
- flag compliance boundaries and unsupported extrapolation explicitly;
- cite external sources with traceable links or identifiers close to the claims they support;
- end with the evidence base, search date, and inference boundary for the field-level assessment.

Save user-facing reports in the environment's designated output directory when one exists; otherwise use the current working directory or the user's requested location. Return a clickable path to the completed file.

## Multi-paper matrix

After completing a single-paper report, ask whether the user wants to continue with other papers and generate a literature matrix. Do not ask again if the user already requested multiple-paper comparison.

The matrix includes only papers successfully skimmed in the current conversation. External sources may explain relationships but do not become matrix rows. If fewer than two papers are available, ask the user to provide another PDF or Markdown paper instead of producing a one-row matrix.

Create a separate Markdown matrix without modifying individual reports. Use exactly these columns: `论文名称`, `研究问题`, `方法`, `数据`, `评价指标`, `核心贡献`, `局限`, `与其他论文的关系`, `对我的研究价值`.

## Completion standard

A report is incomplete if it merely paraphrases the abstract, omits a required section, fails to disclose missing evidence, presents external context without sources, assigns ratings without reasons, or states lifecycle opportunities as established clinical or promotional claims.
