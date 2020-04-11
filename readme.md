# Twitter Search

> Instantly search across your entire Twitter history with a beautiful UI powered by Algolia.

[![Build Status](https://travis-ci.com/saasify-sh/twitter-search.svg?branch=master)](https://travis-ci.com/saasify-sh/twitter-search) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

<a href="https://twitter-search.io">
  <p align="center">
    <img src="https://raw.githubusercontent.com/saasify-sh/twitter-search/master/media/screenshot-search-ui-0.jpg" alt="Screenshot of search UI" />
  </p>
</a>

## Features

- 💯 **Open source**
- 🙈 [Hosted version](https://twitter-search.io) provided by [Saasify](https://saasify.sh)
- 🙉 Self-hosted version is easy to set up
- 🐳 Built using [Algolia](https://www.algolia.com), [Twitter API](https://developer.twitter.com/en/docs), and [ZEIT](https://zeit.co), and
- 💪 Scales "infinitely" via serverless magics
- 🤖 Includes an auto-generated OpenAPI spec
- 👍 Super simple -- Algolia and Saasify do all the hard work for us

## Saasify

**[This entire product](https://twitter-search.io) was built and launched in around 8 hours**.

The only reason it was remotely possible to build a production-quality MVP this quickly was because Saasify handled all of the boring and time-consuming parts, including:

- User accounts
- Stripe billing
- Auto-generated marketing site
- API authentication
- Twitter OAuth
- Rate limiting
- Caching
- Legal docs
- Monitoring
- Lots of glue and book-keeping

The key to Saasify's power is that it handles all of this SaaS boilerplate for you, allowing you to focus solely on your product's **unique value proposition**.

#### Implementation

In the case of [Twitter Search](https://twitter-search.io), its unique value proposition comes in the form of two pieces: a REST API that handles the core functionality ([src/](./src)) and a webapp for the UI ([web/](./web)).

The REST API is written in TypeScript using [Koa](https://koajs.com) and [tsoa](https://github.com/lukeautry/tsoa). Each API endpoint receives some custom headers from Saasify's API proxy that let it know everything about the authenticated user making the request.

These headers include:

- `x-saasify-user` - String ID of the authenticated user making the API call.
- `x-saasify-plan` - String slug of the pricing plan this user is subscribed to.
- Additional headers specific to Twitter OAuth

The embedded webapp can be viewed from the [dashboard](https://twitter-search.io) and is a standard Create React App written in JavaScript. It's embedded in an iframe within Saasify's auto-generated host SPA which informs the webapp of the details for the authenticated user via a small JS script called [saasify-sdk](https://github.com/saasify-sh/saasify/tree/master/packages/saasify-sdk).

Of course, this product's core feature set wouldn't be possible without [Algolia](https://www.algolia.com/) powering the search and [ZEIT](https://zeit.co) hosting the serverless API and embedded static webapp.

#### Looking to the future

This may sound a bit complicated and it's definitely not as simple as we'd like at the moment. Even so, we hope this open source product shows the potential of the platform we're building.

Our team is working very hard to improve the developer experience [open source core](https://github.com/saasify-sh/saasify) that Saasify provides, and we hope to make this type of integration much simpler in the coming months.

Some of the related roadmap items that I'm particularly excited about include:

- A visual template editor that mirrors the Saasify CLI's functionality.
- The ability to **eject** from our hosted SaaS boilerplate and fully customize your product.
- Breaking out the current monolithic React frontend into embeddable blocks that you can use with any website or framework.
- Continuing to build a strong community of successful Indie SaaS makers who have used Saasify to get their ideas to market.

If you want to learn more about how Saasify works and experiment with rapidly launching your own SaaS products, check out the [docs](https://docs.saasify.sh) and feel free to [reach out](https://docs.saasify.sh/#/support).

## License

MIT © [Saasify](https://saasify.sh)
