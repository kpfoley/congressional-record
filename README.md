# Congressional Record

A parser for the Congressional Record.

---

## Supported sources

Currently only the GPO HTML packages are supported. Urls look like this:

<http://www.gpo.gov/fdsys/pkg/CREC-2014-01-21.zip>

Inside this zip is an `html` folder containing the pages of the day's record.
Currently, it's expected that you'll convert those HTML files to plain text, using
only the content between `<pre></pre>` tags before feeding them to this script.
If you'd like to submit a patch that accepts html, that would be great!

## Requirements

- lxml
- python 2.x

## Usage

(Make sure the x-bit is set on parser.py)

`./parser.py`

### Options

- `-id`, `--indir`: Input directory to parse. All .txt files in the dir will be processed.
- `-od`, `--outdir`: Output directory for parsed files. Defaults to __parsed in the input directory.
- `-l`, `--logdir`: Directory for logs to be written to. Defaults to __log in the input directory.
- '--interactive': Interactive mode: Step through files and choose which to parse.
- A positional argument can be provided with a single file to process, rather than iterating through a directory, but if `-id` is provided it will take precedence. Interactive mode is disabled when parsing a single file.

### Examples

```
$ ./parser.py -h

usage: parser.py [-h] [-id INDIR] [-od OUTDIR] [-l LOGDIR] [--interactive]
                 [infile]

Parse arguments for the Congressional Record Parser

positional arguments:
  infile                The file to parse

optional arguments:
  -h, --help            show this help message and exit
  -id INDIR, --indir INDIR
                        An entire directory to traverse and parse, can replace
                        infile
  -od OUTDIR, --outdir OUTDIR
                        An output directory for the parsed content
  -l LOGDIR, --logdir LOGDIR
                        An output directory for logs
  --interactive         Step through files and decide whether or not to parse
                        each one

$ ./parser.py -id ~/Projects/CR/CREC-2014-01-21/txt
flag status: False
saved file /Users/dan/Projects/CR/CREC-2014-01-21/txt/__parsed/CREC-2014-01-21-pt1-PgE109-2.xml to disk
flag status: False
saved file /Users/dan/Projects/CR/CREC-2014-01-21/txt/__parsed/CREC-2014-01-21-pt1-PgE109-3.xml to disk
flag status: False
saved file /Users/dan/Projects/CR/CREC-2014-01-21/txt/__parsed/CREC-2014-01-21-pt1-PgE109-4.xml to disk
...
```