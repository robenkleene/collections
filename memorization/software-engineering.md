# Software Development

- **In an assert statement testing equality, what are the names of the two values being compared?** Expected and actual.
- **When testing equality in an assert statement, which order do the values go in?** Expected then actual.

## Pagination

- **What is classic pagination?** Sending a number of items per page and a current page.
- **What is cursor-based pagination?** The API returns a next cursor used to get the next page of results along with the limit
- **In cursor-based pagination, how do you go back to the previous page?** This isn't usually provided by the API, but the client can keep track of cursors for the previous pages itself.
- **In a pagination API, what is the limit?** The number of items per page
- **What is the advantage of cursor-based pagination?** Prevents results from being skipped or duplicated as the data mutates, more efficient database operations

## Terminology

- **In software engineering, what does ETL stand for?** Extract, transform, load
- **In software engineering, what is an ETL problem?** Extract data from a source, transform it to a new format, load it into a new database
- **In software engineering, what is an example of an ETL problem?**

## CPU

- **Where does `x86` get its name?** Intel 8086
- **What is `x86`?** Instruction set architectures for Intel microprocessors
- **What is `x86_64`?** The 64-bit version of the `x86` instruction set
- **What is `arm64`?** The 64-bit version of the ARM architecture
- **What is `AArch64`?** The 64-bit version of the ARM architecture
- **What is difference between `AArch64` and `arm64`?** They are the same thing
- **What is a CPU?** The part of a computer that executes instructions
- **What is a microprocessor?** A single chip CPU
- **What is the difference between a Microprocessor and a CPU?** A CPU is not necessarily one chip, while a microprocessor is (most CPUs produced today are microprocessors)

## Character Sets

- **What is Unicode?** A standard for mapping code points to characters
- **In Unicode, what is a code point?** A mapping of a value to a character (E.g., `U+0024` for `$`)
- **What are UTF-8 and UTF-16?** Encodings that converts Unicode to binary strings
- **What does UTF-8 stand for?** Unicode Transformation Format (8-bit)
- **What does ASCII stand for?** American Standard Code for Information Interchange
- **What is ASCII?** A character set and encoding that maps 128 digits to letters
- **What is the relationship between ASCII and UTF-8?** UTF-8 uses the same characters for the first 128 digits as ASCII, and the next 128 are the same as Extended ASCII or ISO 8859-1 or Latin-1
- **What does ISO 8859-1 stand for?** International Organization for Standardization (the same one as for ISO in photography)
- **What is Extended ASCII or ISO 8859-1 or Latin-1?** An extension to ASCII that adds one more bit for 256 characters (in particular accented characters)
- **How many characters are in Extended ASCII?** 256
- **How many characters are in ASCII?** 128
- **Since ASCII is 128 characters, and an 8-bit integer holds 256 values, what is the last bit used for?** A parity check (a form of error checking)

### ASCII

- `0-31`: Control characters
- `32-127`: Printable characters
- `128-255`: Extended ASCII characters
