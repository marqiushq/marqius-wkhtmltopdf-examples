# wkhtmltopdf replacement examples: 14 libraries, a one-line switch

[![Render all 14 library examples](https://github.com/marqiushq/marqius-wkhtmltopdf-examples/actions/workflows/render-examples.yml/badge.svg)](https://github.com/marqiushq/marqius-wkhtmltopdf-examples/actions/workflows/render-examples.yml)

**What it is.** Working examples for 14 popular wkhtmltopdf libraries, in Python, PHP, Ruby, JavaScript, Go, Java, Elixir and .NET. Each one makes a real invoice PDF with marqius-wkhtmltopdf, the maintained drop-in replacement for wkhtmltopdf, using the library just as its own documentation shows.

**Why it matters.** wkhtmltopdf is archived, and Debian 13 and Ubuntu 26.04 no longer include it. Switching away from it should be a one-line change, not a rewrite. Here you can see that one line for your library, run it on your own machine and hold the PDF in a few minutes. A workflow runs all 14 examples on every change and checks each PDF.

![marqius-wkhtmltopdf: keep your code, upgrade your PDFs](assets/cover.webp)

## Pick your library

| Library | Language | Example | Manual chapter |
|---|---|---|---|
| python-pdfkit | Python | [examples/python-pdfkit](examples/python-pdfkit/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=7) |
| django-wkhtmltopdf | Python, Django | [examples/django-wkhtmltopdf](examples/django-wkhtmltopdf/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=13) |
| KnpLabs Snappy | PHP | [examples/knplabs-snappy](examples/knplabs-snappy/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=16) |
| laravel-snappy | PHP, Laravel | [examples/laravel-snappy](examples/laravel-snappy/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=18) |
| phpwkhtmltopdf | PHP | [examples/phpwkhtmltopdf](examples/phpwkhtmltopdf/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=20) |
| KnpSnappyBundle | PHP, Symfony | [examples/knp-snappy-bundle](examples/knp-snappy-bundle/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=23) |
| CakePdf | PHP, CakePHP | [examples/cakepdf](examples/cakepdf/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=26) |
| wicked_pdf | Ruby, Rails | [examples/wicked-pdf](examples/wicked-pdf/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=29) |
| PDFKit | Ruby | [examples/ruby-pdfkit](examples/ruby-pdfkit/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=31) |
| wkhtmltopdf for Node | JavaScript, Node.js | [examples/node-wkhtmltopdf](examples/node-wkhtmltopdf/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=33) |
| go-wkhtmltopdf | Go | [examples/go-wkhtmltopdf](examples/go-wkhtmltopdf/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=35) |
| java-wkhtmltopdf-wrapper | Java | [examples/java-wkhtmltopdf-wrapper](examples/java-wkhtmltopdf-wrapper/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=38) |
| pdf_generator | Elixir | [examples/elixir-pdf-generator](examples/elixir-pdf-generator/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=41) |
| Rotativa.AspNetCore | .NET | [examples/rotativa-aspnetcore](examples/rotativa-aspnetcore/) | [Chapter](https://marqius.com/download/developer-manual.pdf#page=44) |

Each folder has its own README: what to install, the one setting that names the program, and how to run it.

## Run your first example

**1. Install marqius-wkhtmltopdf.** You can read the installer before you run it:

```bash
curl -fsSL https://marqius.com/marqius-wkhtmltopdf.sh -o install-marqius.sh
bash install-marqius.sh
```

The installer checks the program it downloads against its published checksum. Homebrew, apt, dnf, apk and Docker work too: see [marqius-wkhtmltopdf](https://github.com/marqiushq/marqius-wkhtmltopdf#install-in-one-minute).

**2. Get the examples:**

```bash
git clone https://github.com/marqiushq/marqius-wkhtmltopdf-examples.git
cd marqius-wkhtmltopdf-examples
```

**3. Run the one for your language.** In Python, for example:

```bash
cd examples/python-pdfkit
python3 -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
python render.py invoice.pdf
```

Open `invoice.pdf`. In the other languages:

| Language | In the example's folder |
|---|---|
| PHP | `composer install`, then `php render.php invoice.pdf` |
| Node.js | `npm install`, then `node render.js invoice.pdf` |
| Ruby | `bundle install`, then `bundle exec ruby render.rb invoice.pdf` |
| Go | `go run . invoice.pdf` |
| Java | Maven's `exec:java`, with `Smoke` as the main class |
| Elixir | `mix deps.get`, then `mix run render.exs invoice.pdf` |
| .NET | The Rotativa example is an ASP.NET Core MVC app: see its README |

The Laravel and Symfony examples go into an existing application: their READMEs, and `scripts/run-php.sh`, show how to set one up.

## What "drop-in" means

Your app keeps calling its PDF library exactly as it does today. marqius-wkhtmltopdf is the program that library starts. If your settings name the path of wkhtmltopdf, you change that one setting; the example for your library shows where. If nothing names it, give marqius-wkhtmltopdf the name `wkhtmltopdf` with `sudo marqius-wkhtmltopdf install`, and nothing changes at all.

## Will my PDFs come out the same?

You can check, in public and on your own templates:

- **[Library tests](https://github.com/marqiushq/wkhtmltopdf-library-tests):** the test suites of 15 wkhtmltopdf libraries, written by their own authors, run with wkhtmltopdf 0.12.6 and with marqius-wkhtmltopdf on every release, with signed results.
- **[Parity suite](https://github.com/marqiushq/wkhtmltopdf-parity):** 86 documents through both programs on every release, every PDF compared, misses included. Run it on your own templates; nothing is uploaded.
- **[Parity check](https://github.com/marqiushq/wkhtmltopdf-parity-check):** the same comparison in your CI, on every pull request.
- **[One invoice, side by side](https://marqius.com/download/launch-2026-11-20/marqius-wkhtmltopdf-same-html-comparison.pdf):** the same HTML through both programs, with both full pages and the method.

## What these examples do not cover

- They cover libraries that start the wkhtmltopdf program. Bindings that load the `libwkhtmltox` library directly, such as DinkToPdf, need a different integration.
- A custom table-of-contents XSL style sheet is not applied. The [developer manual](https://marqius.com/download/developer-manual.pdf) lists every difference.
- They use sample HTML. For documents from people you don't know, read the [security guidance](https://marqius.com/wkhtmltopdf/security/) first.

## Licence

The example code here is open source under the MIT licence. marqius-wkhtmltopdf is proprietary software from Simple AI LLC under its own [licence](https://marqius.com/wkhtmltopdf/licence-agreement/); this repository holds examples, not the program. It is free for 30 days with no card, and personal, teaching and open-source use is free with a Community licence. Anything done by or for a business, including internal tools and client work, needs a paid plan once the trial ends. [See the plans and prices](https://marqius.com/licence/marqius-wkhtmltopdf).

★ **Star this repository** if an example saved you time.
