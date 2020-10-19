## EJS PARTIALS

Partials. They're like html functions, snippets of html that will be constantly reused page after page of a website.

> <%- include( PARTIAL_FILE ) %> is the exact code bit - you swap in the name of the file at ( PARTIAL FILE ), removing the () as well - and you insert that line of code in your html, and which point EJS will go and grab what is in that html file, and render/populate it out there.

I'm uncertain why it's called a partial, instead of module/segment/snippet, but those are all just synonyms for what is happening: write once, read everywhere, but for html pieces, via EJS. I like to think of it as html modules, becuase this make a website, or _any_ website for that matter, very modular. If something needs to be moved, instead of rooting around every page and making those details over and over, you go to the partial file, make the change, confirm it all continues working as such, and you're set. It doesn't mean other issues won't arise, as css is going to be css, and likely find something to bump, requiring other changes, but if you set them all up as partials, it should still just be write once, modify once, read everywhere. Another instance of DRY code philosophy - Don't Repeat Yourself. And I'm all for it.

The [tutorial video](https://www.youtube.com/watch?v=3_xEEH4fTEk&t=0s&index=7&list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt) lays it out cleanly and simply, so it's a good starter/refresher to see partials in action.
