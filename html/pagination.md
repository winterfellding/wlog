### Pagination with Struts2 & jQuery pagination plugin

We can consider pagination as two part, `front-end` and `back-end`.

In `front-end`, we declare an ul and use `jquery-pagination-plugin` to create a pagination list, and define the event which triggered by `click`, and save the curPage in the form, and submit the form.

In `back-end`, we get the current pageNumber, and pageSize as we defined when we first
load the page the first time, we can get the right collection of records as send them back to the web page.