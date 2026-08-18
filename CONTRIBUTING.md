# Contributing

Contributions to this book are genuinely welcome. It began as a set of personal notes, and
every reader who knows more than the author about some corner of the subject makes the next
edition better.

There are three ways in: report something, propose something, or write something.

## How this repository works

The book is written in Microsoft Word. The `document/` folder holds the manuscript
(`Aerobatics_Principles-Marco_Blackbird_Merli.docx`) and the current edition exported from it
(`Aerobatics_Principles-Marco_Blackbird_Merli.pdf`). The `.docx` is the single source of
truth - there is no other master copy anywhere.

One practical consequence: **the `.docx` cannot be merged.** Git tracks it as an opaque
binary, so two people editing it in parallel produce two versions and no way to reconcile
them. Only one person edits the manuscript at a time.

## Reporting an error

Open an [issue](https://github.com/yohji/aerobatics-principles/issues). Useful reports
include the version of the document, the section, and - for anything technical - a reference
if you have one. A technical error is worth reporting even if you are not certain about it:
an unclear passage is a defect regardless of who is right.

Three kinds of report are especially valuable:

- **Something is wrong.** A figure described incorrectly, a mechanism explained the wrong way
  round, a procedure whose steps are out of order.
- **Something is unclear.** If a passage had to be read twice, that is a defect.
- **Something is missing.** A concept the book relies on but never explains.

## Contributing actively

If you want to do more than point at a problem - rewrite a section, add a figure that is
missing from the catalogue, contribute a diagram, work on an entire chapter - that is very
welcome, and there are two routes.

**By pull request.** Fork the repository and open a pull request. For everything that is not
the manuscript - the README, this file, the preview images, a broken link - it works exactly
as you would expect, and the change is merged.

For the manuscript itself, a pull request cannot be merged automatically, since Word documents
have no meaningful diff or merge. Open one anyway if that is how you prefer to work: attach
your edited `.docx` with tracked changes turned on, or write the proposed text in the pull
request description. It will be reviewed there and applied to the master document by hand,
and you will be credited in the change log.

**By direct contact.** If pull requests are not your world - and there is no reason they should
be, this is a book about flying - simply write to **marcomerli@marcomerli.net**. A description
of what you think should change, a rewritten paragraph in the body of an email, a photograph of
a page with notes on it: all of it is usable. Substance matters, the format does not.

Either way, please say how you would like to be credited, or whether you would rather not be.

## Translating

The licence (CC BY-NC-SA 4.0) allows translations and adaptations. If you want to make one:

1. Start from the `.docx` in `document/`, not from the PDF. Fork the repository and you have the
   working document as it stands.
2. Keep the licence. Derived work must carry the same CC BY-NC-SA 4.0 terms.
3. Keep the Disclaimer, translated along with the rest. This matters more than anything else
   in this file: the book describes stalls, spins and their recoveries, and it is written for
   flight simulation only. That statement must travel with the content.
4. Make clear that yours is a derived version and not the original edition.
5. Open an issue, or write to the address above, when it is ready and it will be linked from
   the README.

Translations are linked, not hosted here. Each translator remains responsible for the accuracy
of their own version, which on a subject like this one is the only sensible arrangement.

## Making a release

For the maintainer, so the steps stay consistent from one edition to the next:

1. Edit the `.docx` in `document/` with Word. Accept any tracked changes and update the table of
   contents before exporting.
2. Update the Change Log table inside the document, and `CHANGELOG.md` in this repository,
   with the same wording.
3. Export the PDF from Word - not from another converter, so that the Aresti symbols and the
   page layout come out as intended - over the existing file in `document/`.
4. Commit both files together, so that the PDF in the repository always matches the manuscript
   beside it.
5. Tag and publish, attaching the PDF:

      git add . && git commit -m "vN" && git push
      gh release create vN \
         "document/Aerobatics_Principles-Marco_Blackbird_Merli.pdf" \
         "kneeboard/Aerobatics_Principles-Exercises.png" \
         --title "vN" --notes-file CHANGELOG.md

6. Refresh the images in `preview/` if the pages they show have changed.
