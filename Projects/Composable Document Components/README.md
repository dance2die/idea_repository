# What?

Composable document components is a way to create "components", which you can use to compose a whole new document(ation/tutorial/books/courses/video courses/MOOC, etc), "doc(s)" hereafter.

# Why?

Any docs are created from scratch or when quoted, they are manually creditted.

When someone, be it a learner/teacher ("user", hereafeter) have a goal (what to learn, what to share/teach),
the user has to create docs from scratch and time consuming.

## What Issues does it solve?

1. Error prone - Human error is huge
1. Time consuming - requires multiple drafts and edits
1. Manual - If one can automatically insert a "component", then it's quick & easy
   - Fast
   - Can be automated
   - Can be tested
   - Can add toolling support

# How?

According to [Atomic Design][atomic design] by [Brad Frost][brad frost], there are four elements that make up a site.

1. Atoms - Smallest building blocks, such HTML tags as form label, input, anchor, etc.
1. Molecules - Provides a function
1. Organisms - Provides a purpose
1. Templates - Provides "contexts" stiching each purposeful organism on the site
1. Pages - Actualized instance of the template.

In term, "docs" can be composed into such form as follows.

1. Atoms - a letter, a number, a symbol, a morse code, gesture, a video, an image
1. Molecules - a word, number with more than 1 digit, a series of symbols, a series of morse code "clicks".
1. Organisms - a sentence, a math forumula, a sign language (movement?), a code snippet
1. Templates - paragraphs, math proof, a function in code, a chapter in a book
1. Pages - a blog post, an article, a book, a video course

This means, when you add "Atoms" component, then the doc would contain only a letter, number or a symbol, etc.  
If "Molecules" component is added to the doc, it's a series of atoms and so on.

We can expose these building blocks for docs to import and have appropriate credit applied automatically.

## A rough technical implementation?

Each component must contain following metadata. (Borrowing GraphQL type definition)

```graphql
type Metadata {
  # Enables auto credit at the doc.
  credit: [AuthorNames]!
  # Automatically fetches the content from here
  source: [URI]!
  # MediaType === MimeType, such application/json, text/plain, etc
  # Instructs a parser, how to treat the data
  mediaType: MediaType!
  # What we are after.
  content: [Content]!

  createdOn: Date
  modifiedOn: [Date]
}

# I am not sure how to represent an exclusive condition of uri & body in graphql.
type Content {
  uri: String
  body: String
}
```

## Knowledge Repository

Kind of like a central hub like, NPM registry/Docker Hub/Nuget registry, from which users can "pull" components and add to the doc.

Maybe a site, from which each component can be clicked on, and paste into

[atomic design]: https://bradfrost.com/blog/post/atomic-web-design/
[brad frost]: https://bradfrost.com/
