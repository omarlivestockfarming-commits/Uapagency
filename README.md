# UAP Agency Demo — Deploy Instructions

This folder is ready to deploy to Netlify with a working AI chatbot,
WITHOUT exposing your Groq API key publicly.

## Folder structure (don't change this)
```
netlify-deploy/
├── index.html              ← your landing page
└── netlify/
    └── functions/
        └── chat.js         ← hides your Groq key, talks to Groq for you
```

## How to deploy

1. Go to https://app.netlify.com and log in (or sign up free)
2. Drag and drop this WHOLE FOLDER (netlify-deploy) onto the Netlify
   dashboard where it says "Drag and drop your site folder here"
3. Netlify will give you a live URL like: random-name-123.netlify.app
   (You can rename it later in Site settings → Change site name)

## CRITICAL — Add your Groq API key (do this or the chat won't work)

1. Get a free key at https://console.groq.com/keys (sign up, then
   click "Create API Key", copy it)
2. In Netlify: go to your site → Site configuration → Environment
   variables
3. Click "Add a variable"
   - Key:   GROQ_API_KEY
   - Value: (paste your Groq key here)
4. Click Save
5. Go to Deploys tab → click "Trigger deploy" → "Deploy site"
   (this restarts your site so it picks up the new key)

That's it. Your key now lives safely on Netlify's servers — it's
never sent to anyone viewing your page, even if they view page source.

## Testing it works

Open your live Netlify URL, tap the chat bubble bottom-right, and
ask it something like "how much does this cost?" — it should reply
within a couple seconds. If it shows the fallback "having trouble
connecting" message, double check the GROQ_API_KEY variable name is
typed exactly right (case-sensitive) and that you redeployed after
adding it.

## Reusing this for client demos

To make a version for a specific client (e.g. a restaurant you're
pitching), just edit the BUSINESS_INFO block near the bottom of
index.html with their real details, then drag-and-drop a fresh copy
of this folder as a NEW Netlify site (so each client demo gets its
own link). The netlify/functions/chat.js file can stay exactly the
same — just remember to add the GROQ_API_KEY environment variable
again on each new site.
