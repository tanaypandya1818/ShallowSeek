## Data Format

*The Natural History* by Pliny the Elder is a series of 37 books, each having multiple chapters. The data in this folder is scraped from the [Perseus Digital Libary](http://www.perseus.tufts.edu/hopper/).

The content of each chapter is stored in JSON in the following format:
```json
{
  book_title: string,
  url: string,
  chapter_name: string,
  paragraphs: string[], 
  footnotes: {
    [string]: string
  }
}
```
where:
- book_title: the title of the book containing this chapter
- url: the url to the PDL page for this chapter
- chapter_name: the name of this chapter
- paragraphs: a list of each paragraph in the chapter
- footnotes: an object containing the footnotes for each chapter. Each key is the footnote number, starting at 1, and the value is the footnote itself.

Each chapter is split into its component paragraphs to create individual documents for RAG, following the process described by [Pataranutaporn, P., Danry, V., Blanchard, L., Thakral, L., Ohsugi, N., Maes, P., & Sra, M. (2023, March)](https://dl.acm.org/doi/pdf/10.1145/3581641.3584065)

The actual content of each chapter and the footnotes are separated, as the footnotes are not written by Pliny the Elder and provide corrections or other information that would not have been available during Pliny's time. To preserve the presence of each footnote, the location where a footnote would have been is denoted with `<@n>` with `n` being the footnote number (1-indexed). These markers can be removed or replaced with the footnote content as desired.