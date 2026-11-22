# Casdesk

Casdesk is an open-source, self-hosted live chat for websites, with AI replies: a small chat widget for your pages, and an inbox where your team answers the visitors. One Casdesk server serves many websites.

**See it live**: the chat bubble at the bottom right of [casdoor.ai](https://casdoor.ai) and [www.casdoor.com](https://www.casdoor.com) is Casdesk. It answers Casdoor's visitors every day.

> **The source code is coming soon.** Casdesk runs in production for our own sites, and we are getting it ready to publish here under the Apache-2.0 license. Star or watch this repository to know when it lands, and [open an issue](https://github.com/casdesk/casdesk/issues/new) to tell us what you would use it for or what it must have.

## Features

- **One line to embed**: a plain script of about 15 KB gzipped, in a shadow root so it never clashes with your page's CSS. No iframe, no third-party cookies.
- **Many sites, one inbox**: each site has its own logo, color, light or dark theme, greeting, domains, agents and notifications.
- **AI replies from your own knowledge**: when no agent is online, or nobody replies in time, an AI answers from the documents you write or import for the site, through any OpenAI-compatible API. It says so when the knowledge does not cover a question, and hands the conversation to a person.
- **AI triage**: the AI tells real questions from greetings, off-topic chats and spam, so your team is only notified about conversations that need a person. Block a visitor or an IP address in one click.
- **Real time**: messages, typing and read receipts are pushed by long polling, which goes through any proxy or CDN.
- **Never miss a visitor**: a message nobody reads within a minute is emailed to the site's agents; a reply the visitor has not seen is emailed to them, with a link back to the conversation.
- **Visitor context**: the page the visitor is on, where they are from (by IP address), the pages they visited, and an optional screen recording of their visit, with every input field masked.
- **Webhooks**: called when a conversation starts, with the same fields as Tawk.to's `chat:start`, so existing alerts (phone calls, chat bots) keep working.
- **Signed-in visitors**: pass your user's ID with an HMAC, and agents see who they are; the user gets the same conversation on every device.
- **Single sign-on for agents** through any OpenID Connect provider ([Casdoor](https://casdoor.ai), Keycloak, Google...), or plain passwords.
- **English and Chinese**, for the widget and the console.
- **One Go binary**: SQLite out of the box, or MySQL. Or Docker.

## Embedding the widget

```html
<script src="https://chat.example.com/widget.js" data-site="example" async></script>
```

| Attribute | Meaning |
| --- | --- |
| `data-site` | The site's name (required) |
| `data-lang` | `en` or `zh`; by default the site's setting, or the visitor's browser language |
| `data-launcher="false"` | Hides the round button; open the chat from your own button with `Casdesk.open()` |

The page's script can call `Casdesk.open()`, `Casdesk.close()`, `Casdesk.toggle()` and `Casdesk.setUser({ id, username, name, email, hash })`. Each site also has a page of its own, `https://<server>/chat/<site>`, to link to from "Contact us".

## Why another live chat

We used Tawk.to, and wanted a chat we could run on our own servers, that answers with AI from our own documents, does not ring our phones for spam, and signs agents in with our own identity provider. So we wrote Casdesk, small enough to run next to any website.

## Feedback

Questions, ideas and feature requests are welcome in [Issues](https://github.com/casdesk/casdesk/issues).

## License

[Apache-2.0](LICENSE)
