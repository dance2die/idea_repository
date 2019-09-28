# What is this?

As I was reading https://www.howtographql.com/graphql-js/8-filtering-pagination-and-sorting/,
I wanted to ask a question by leaving a comment at a specific section, which can be answered there right where the question is asked.

![links length?](images/links-length.png)

But there isn't a way to leave a comment not to mention right at that location.

# How is this beneficial?

Many blogs are to share news and teach others. When readers have a question many blogs have a way to leave a comment at the bottom but the context is either lost or hard to associate it with the content, unless a commentor copies text from the article or take a screenshot of it.

Leaving the comment for a question, thoughts, etc would provide a better context without having to scroll to the content.

Or each paragraph can have an `id` tag a user can copy and paste in the comment at the end...(if leaving a comment in-line can't work)

# When does this fail?

This could add a blog to the blog page size. Depending on the implementation, dynamic feature loading might not be available.

As this style of commenting is not a standard practice, people could be confused as to how to leave a comment as we are trained to scroll to the bottom to leave a comment...  
_Need to figure out how to make it more intuitive_

# Accessibility Concerns?

a11y is not my strong suit. The best I can do for now is to run [Axe][axe] and follow the recommendations thereof.

# Suggestions?

1. GitHub style comment on the line.
   ![github comment style](images/github_style.gif)

- **Up**: Easy to leave a comment & reply. Easy to spot.
- **Down**: Hard to implement as HTML text flows unlike code samples above.

1. Google Doc style comment
   ![google doc style](images/google_doc_style.gif)

- **Up**: Doesn't change the flow of the page & comment stands out
- **Down**: Harder to use - Need to highlight for the "comment" button to show up.

# Compromise? ('tween Github & Google Doc styles)

On hover of a paragraph, add the "+" as GitHub shows, but instead of leaving the comment in-line disrupting the flow of the content, add the comment on the right like Google Doc does.

# Implementation Brainstorm?

1. Vanilla JS
   - Framework agnostic?
   - Isomorphic?
1. React
   - How to inject to `<p />`?
   - A hook? A component factory? 🤔
1. Gatsby - Create a plugin to wrap each paragraph.
   - [wrapRootElement][wraprootelement] - Provide the whole site with the comment system
   - [wrapPageElement][wrappageelement] - Provide the per-page level comment

# Additional Info?

Readers should be able to hide comments or `+` for leaving comments?

[wraprootelement]: https://www.gatsbyjs.org/docs/browser-apis/#wrapRootElement
[wrappageelement]: https://www.gatsbyjs.org/docs/browser-apis/#wrapPageElement
[axe]: https://www.deque.com/axe/
