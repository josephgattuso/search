# Search

> Designing a front-end for Google Search, Google Image Search, and Google Advanced Search.

## Background

For this project, we’ll write forms that send data to an existing web server: in this case, Google’s.

When you perform a Google search, as by typing in a query into Google’s homepage and clicking the “Google Search” button, how does that query work? Let’s try to find out.

Navigate to <https://www.google.com>, type in a query like “Aardvark” into the search field, and click the “Google Search” button.

As you probably expected, you should see Google search results for “Aardvark.” But now, take a look at the URL. It should begin with <https://www.google.com/search>, the route on Google’s website that allows for searching. But following the route is a `?`, followed by some additional information.

Those additional pieces of information in the URL are known as a query string. The query string consists of a sequence of GET parameters, where each parameter has a name and a value. Query strings are generally formatted as

```url
field1=value1&field2=value2&field3=value3...
```

where an `=` separates the name of the parameter from its value, and the `&` symbol separates parameters from one another. These parameters are a way for forms to submit information to a web server, by encoding the form data in the URL.

Take a look at the URL for your Google search results page. It seems there are quite a few parameters that Google is using. Look through the URL (it may be helpful to copy/paste it into a text editor), and see if you can find any mention of “Aardvark,” our query.

If you look through the URL, you should see that one of the GET parameters in the URL is `q=Aardvark`. This suggests that the name for the parameter corresponding to a Google search is `q` (likely short for “query”).

It turns out that, while the other parameters provide useful data to Google, only the `q` parameter is required to perform a search. You can test this for yourself by visiting <https://www.google.com/search?q=Aardvark>, deleting all the other parameters. You should see the same Google results!

Using this information, we can actually re-implement a front end for Google’s homepage. Paste the below into an HTML file called `index.html`, and open it in a browser.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Search</title>
  </head>
  <body>
    <form action="https://google.com/search">
      <input type="text" name="q" />
      <input type="submit" value="Google Search" />
    </form>
  </body>
</html>
```

When you open this page in a browser, you should see a (very simple) HTML form. Type in a search query like “Aardvark” and click “Google Search”, and you should be taken to Google’s search results page!

How did that work? In this case, the `action` attribute on the `form` told the browser that when the form is submitted, the data should be sent to `https://google.com/search>. And by adding an `input`field to the form whose`name`attribute was`q`, whatever the user types into that input field is included as a GET parameter in the URL.

Your task in this project is to expand on this site, creating your own front end for Google Search, as by exploring Google’s interface to identify what GET parameters it expects and adding the necessary HTML and CSS to your website.

## Getting Started

- Download the distribution code from <https://cdn.cs50.net/web/2020/spring/projects/0/search.zip> and unzip it.

## Specifications

Your website must meet the following requirements:

### 1. Pages

Your website should have at least three pages: one for Google Search, one for Google Image Search, and one for Google Advanced Search.

- On the Google Search page, there should be links in the upper-right of the page to go to Image Search or Advanced Search. On each of the other two pages, there should be a link in the upper-right to go back to Google Search.

### 2. Query Text

On the Google Search page, the user should be able to type in a query, click “Google Search”, and be taken to the Google search results for that page.

- Like Google’s own, your search bar should be centered with rounded corners. The search button should also be centered, and should be beneath the search bar.

### 3. Query Images

On the Google Image Search page, the user should be able to type in a query, click a search button, and be taken to the Google Image search results for that page.

### Query Advanced

On the Google Advanced Search page, the user should be able to provide input for the following four fields (taken from Google’s own [advanced search](https://www.google.com/advanced_search) options)

- Find pages with… “all these words:”
- Find pages with… “this exact word or phrase:”
- Find pages with… “any of these words:”
- Find pages with… “none of these words:”

### Appearance

Like Google’s own Advanced Search page, the four options should be stacked vertically, and all of the text fields should be left aligned.

- Consistent with Google’s own CSS, the “Advanced Search” button should be blue with white text. When the “Advanced Search” button is clicked, the user should be taken to search results page for their given query.

### Lucky

Add an “I’m Feeling Lucky” button to the main Google Search page. Consistent with Google’s own behavior, clicking this link should take users directly to the first Google search result for the query, bypassing the normal results page.

- Aesthetics The CSS you write should match Google’s own aesthetics as best as possible.

## Hints

- To determine what the parameter names should be, you’re welcome to experiment with making Google searches, and looking at the resulting URL. It may also be helpful to open the “Network” inspector (accessible in Google Chrome by choosing View -\> Developer -\> Developer Tools) to view details about requests your browser makes to Google.

  - Any `<input>` element (whether its `type` is `text`, `submit`, `number`, or something else entirely) can have `name` and `value` attributes that will become GET parameters when a form is submitted.
  - You’re may also find it helpful to look at Google’s own HTML to answer these questions. In most browsers, you can control-click or right-click on a page and choose “View Page Source” to view the page’s underlying HTML.

- To include an input field in a form that users cannot see or modify, you can use a [“hidden”](https://www.w3schools.com/tags/att_input_type_hidden.asp) input field.
