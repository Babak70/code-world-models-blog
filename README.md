# Debugging Code World Models

A blog post analyzing state-tracking capabilities in Code World Models (CWMs).

## Associated Paper

- arXiv: https://arxiv.org/abs/2602.07672
- PDF: https://arxiv.org/pdf/2602.07672

BibTeX:

```bibtex
@misc{rahmani2026debuggingcodeworldmodels,
	title={Debugging code world models},
	author={Babak Rahmani},
	year={2026},
	eprint={2602.07672},
	archivePrefix={arXiv},
	primaryClass={cs.SE},
	url={https://arxiv.org/abs/2602.07672},
}
```

## Analytics and Comments

This blog uses two lightweight, free integrations:

- **GoatCounter** for pageview analytics (GitHub Pages friendly)
- **Utterances** for comments (backed by GitHub Issues)

### GoatCounter (pageviews)

1. Create a GoatCounter site: https://www.goatcounter.com/
2. In the HTML pages, replace `YOUR_GOATCOUNTER_CODE` in the script tag with your site code.

### Utterances (comments)

1. Install/configure the Utterances GitHub App for your repo: https://utteranc.es/
2. Comments are embedded via a script tag configured with `repo="Babak70/code-world-models-blog"`.
	The discussion thread is keyed by `issue-term="pathname"`.

## View the Blog

**Live:** [https://babak70.github.io/code-world-models-blog/posts/state-tracking-code-world-models.html](https://babak70.github.io/code-world-models-blog/posts/state-tracking-code-world-models.html)

Or serve locally:

```bash
python3 -m http.server 8080
```

Then visit: http://localhost:8080/posts/state-tracking-code-world-models.html

## Structure

- `posts/` - Blog post HTML
- `styles/` - CSS stylesheets
- `assets/images/` - Figures and plots
- `assets/reports/` - Detailed failure analysis reports (CruxEval, HumanEval, Nesting)

## Author

[Babak Rahmani](https://scholar.google.com/citations?user=Q3DLZlEAAAAJ&hl=en)
