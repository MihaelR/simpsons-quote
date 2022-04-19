# Experience day exercise

⚠️ Blitzstack works best in Chrome (images are broken in Firefox (CSP header))

## Setup

To start and work on the case please do the following:

- clone the repo to your machine
- **NEVER** push to this repo (some other candidates might steal your brilliant ideas)
- `npm install` as usual and start the project `npm run dev`
- look at the code and get familiar with it
- you have tailwind already set up for you, but you can also use pure CSS (just make sure, that you do not mix)
- please stop/record the time you work on the assignment. It should be less than 4h. If you cannot finish within 4 hours, just stop anyway, we still have enough code to talk about. (just be honest to yourself and us and keep the times "real" ;) )
- Bring your solutions to the tech interview session. You can share your screen in our meeting (MS Teams), or you can setup a online "editor" (we recommend blitzstack.com)

When you finish the assignment, we will set up (probably already have) a tech interview (approx. 1h), where we discuss the solutions and topics around the challenges. There is no (perfect) score for the assignment. We will use it mainly for a base of discussion.

It also should be a little fun to work with code. So do not worry, and have fun.

## The Story

Our client has a VERY simple website.
He loves the simpsons. And he wants to show some quotes of the simpson characters on his website.
Since he knows some HTML and CSS he already started the project. But then gave up.
You pick up from here.

## Your challenges

### 0.) Center the headline

As a little warm up:

- horizontally center the headline "Simpson Quotes" in the page.
- center the quote under the image
- output the name of the character as well (you choose any "design")

### 1.) Fetch quotes from api

The client used some dummy data in the `List.vue` file. Make a request to the Api and fetch 10 items and display all of them (do not worry about layout yet).

### 2.) Responsive layout

The client requests a responsive layout:

- on mobile: all cards full width (keep some margins to the edges)
- on tablet: 3 cards in one row
- on desktop: 5 cards in one row, and also the image of the character should be on the left side of the card and the quote on the right)

(hint: use reasonable sizes for the viewports; up to you; maybe a "container" will be good for very large screens)

### 3.) Buttons to load 5, 10, 15 quote

The client requests 3 buttons on the bottom of the page.

- Text: "5 Quotes are good" if you click on it fetches 5 Quotes
- Text: "10 Quotes are better" if you click on it fetches 10 Quotes
- Text: "15 Quotes are the best" if you click on it fetches 15 Quotes

You are free to "design" the buttons as you like.
(hint: later we will discuss what you picked (e.g. `<button> vs <a>`))

### 4.) Make it sort

At the top of the file, you will find 2 "Buttons" for sorting. The component was already created, but the client couldn't get it to work.

- make the 2 buttons work
- keep one separate component and use it twice
- then the sorting is active, the button should somehow be "highlighted" (you choose the style)

### 5.) No Code question / discussion

This challenge is not about code. You do not have to write any code. But read the bullet points and think about the questions and maybe write some short notes about it. We will discuss these topics in our session.

- After we implemented the "load 5/10/15" buttons, we found out, that when the user clicked the buttons multiple times, the API was crashing under the load of too many requests. Prepare an idea (or multiple?) how to prevent the user from sending too many requests to the API. Bring your ideas in "words" / bullet points to the interview. (no code needed)
- After we deploy our nice website, we found out, that we have some accessibility issues. Can you find some issues about accessability and do you know how to address them? What can we do to make our site more accessible. (Please do not change your code at this point. We never had Accessibility as a requirement, so it's OK to have these issues)
- Think about the current state of the application. What did the client forget? What issues or ideas do you have as a developer, to make the site more stable and robust. We will discuss.
