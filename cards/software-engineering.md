# Software Development

- **In an assert statement testing equality, what are the names of the two values being compared?** Expected and actual.
- **When testing equality in an assert statement, which order do the values go in?** Expected then actual.

## Pagination

- **How is pagination without a pagination token implemented?** By sending up a current page and number of items per page
- **How is pagination implemented with a pagination token?**
- **Why are pagination tokens used?** Because if the results have changed between calls the then items can end up duplicated or skipped.
