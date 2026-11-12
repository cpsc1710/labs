# CPSC 1710 Labs

Student-facing assignments and starter materials for CPSC 1710, Fall 2026.

## Labs

- [Lab 1: Meet a deep-learning notebook](lab-01/)
- [Lab 2: From one pixel to your classifier](lab-02/)
- [Lab 3: MNIST, and what the code is doing](lab-03/)
- [Lab 4: Your first model API calls](lab-04/)
- [Lab 5: Read a GPT, write pseudocode](lab-05/)
- [Lab 6: Watermarking text with a secret key](lab-06/): Parts 1 and 2 form the core lab; Parts 3–5 are optional and collapsed by default
- [Lab 7: A tiny agent](lab-07/): build a small agent in Colab and run it with models from frontier size down to a tiny one

- [Lab 8: Feedback and leverage points](lab-08/): a mobile thermostat reproduction and a separate ranking-and-matching activity, with source credits and QR codes, plus a linked live classroom ranking; the Thursday lab runs an agent on Prosus Vending Bench in Colab (`vending-bench.html`, `vending-bench.ipynb`)

Use the [live course hub](https://cpsc1710.github.io/labs/) for the simplest experience. Each assignment is available as a webpage and a printable PDF.

## Guides

- [One folder for the whole course](course-folder/): set up a course folder for Codex or Claude Code, with the `grill-me` midterm practice skill

## Opening the files

The HTML files have no build step. After cloning, open `index.html` directly in Chrome, Safari, or Firefox. Avoid VS Code's **Open Preview** for these files: its internal `file+.vscode-resource` links do not work as normal browser addresses.

You can also serve the repository locally:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000/`.

## Credits

Materials are by [Xiuye Chen](https://github.com/xiuyechen) and shared under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
