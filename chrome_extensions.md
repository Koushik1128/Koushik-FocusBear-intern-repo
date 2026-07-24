# Chrome Extensions for Dev Productivity

# Chrome Extensions for Dev Productivity

## Which extensions did I install? Why?

I installed all four suggested ones: React Developer Tools, Redux DevTools, a JSON Viewer, and Lighthouse.

**React Developer Tools** made sense to grab first since a lot of the tools and dashboards I've been poking around during onboarding (like the Focus Bear dashboard itself) are built with React. Instead of trying to guess what's going on just by looking at the rendered page, I can actually open DevTools and see the component tree, what props and state each piece has, and even how long things take to re render. It feels like getting to look under the hood instead of just staring at the outside of the car.

**Redux DevTools** felt like a natural pair with React DevTools. If an app is using Redux for state management, this lets me see every action that fired and exactly how the store changed after each one, basically a full history instead of me manually sprinkling `console.log` everywhere and losing track of what changed when.

**JSON Viewer** was more of a small quality of life thing. Anytime I hit an API endpoint directly in the browser, the raw JSON used to come back as one long unreadable line. Now it auto formats it with indentation and lets me collapse sections, so scanning through a response actually takes seconds instead of me manually eyeballing brackets.

**Lighthouse** I installed mainly because it was on the list, but it turns out Chrome already has Lighthouse built into DevTools by default under its own tab. So the extension itself doesn't really add new capability, it just gives a one click shortcut from the toolbar instead of having to open DevTools first. Still handy, just less "new" than I expected.

## What was the most useful thing I learned?

Honestly, the biggest thing I took away wasn't about any one extension, it was realising how much I've been relying on `console.log` as my default debugging habit. Having React DevTools and Redux DevTools actually show me the live component tree and the full action/state history means I don't have to guess what's happening or manually trace it through scattered print statements anymore. It's a small shift, but it changes debugging from "add a log, refresh, check console, repeat" into just looking at the current state directly. Also good to know that some of these tools (Lighthouse specifically) are already sitting inside DevTools by default, so it's worth checking what's already built in before assuming I need an extension for everything.

