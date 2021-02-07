# Software Development

- **In an assert statement testing equality, what are the names of the two values being compared?** Expected and actual.
- **When testing equality in an assert statement, which order do the values go in?** Expected then actual.

## Pagination

- **What is classic pagination?** Sending a number of items per page and a current page.
- **What is cursor-based pagination?** The API returns a next cursor used to get the next page of results along with the limit
- **In cursor-based pagination, how do you go back to the previous page?** This isn't usually provided by the API, but the client can keep track of cursors for the previous pages itself.
- **In a pagination API, what is the limit?** The number of items per page
- **What is the advantage of cursor-based pagination?** Prevents results from being skipped or duplicated as the data mutates, more efficient database operations
