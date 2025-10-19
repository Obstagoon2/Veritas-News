# Veritas News

> A modern, serverless news aggregator that uses the Gemini API to analyze news from multiple viewpoints and deliver an unbiased summary.

[**Live Demo**](https://www.google.com/url?sa=E&source=gmail&q=https://your-username.github.io/veritas-news/)   •   [**Setup Guide**](https://www.google.com/search?q=%23setup-and-deployment-guide)

## Screenshot

## Features

  * **AI-Powered Summaries:** Uses the Gemini API with Google Search grounding to find and analyze multiple sources on a single news topic.
  * **Unbiased Reporting:** Delivers a structured analysis including a neutral summary, points of contention between sources, a bias breakdown, and a "likely truth" synthesis.
  * **User Accounts:** Secure sign-up and login functionality powered by Firebase Authentication.
  * **Personalization:**
      * Users can follow specific news genres.
      * A personalized homepage feed aggregates top stories from a user's followed genres.
      * Saves user preferences for light/dark mode.
      * Supports location-specific "Local News."
  * **Dynamic Story Discovery:** Fetches lists of current top stories for each genre.
  * **Modern & Responsive UI:** Clean, dark-mode-first interface built with Tailwind CSS that works seamlessly on desktop and mobile devices.
  * **Zero Backend Maintenance:** A completely serverless architecture running on client-side JavaScript.

## Tech Stack

  * **Frontend:** HTML, Tailwind CSS, Vanilla JavaScript
  * **Backend Services:**
      * **Firebase Authentication:** For user management.
      * **Firestore:** For storing user preferences (genres, theme, location).
      * **Google Gemini API:** For all news aggregation and analysis.

## How It Works

1.  **Story Discovery:** When a user clicks a genre, a request is sent to the Gemini API asking for a list of top story titles for that category. For logged-in users, it requests one story from each of their followed genres.
2.  **Analysis Request:** When a user clicks a specific story title, a detailed request is sent to the Gemini API, instructing it to act as an unbiased news analyst.
3.  **AI Analysis:** Gemini uses its Google Search tool to find multiple articles about the topic from different perspectives. It then synthesizes this information based on the prompt's instructions.
4.  **Display:** The final, formatted markdown response from the API is parsed into clean HTML and displayed to the user. All user-specific data (like saved genres or location) is securely fetched from Firestore.

## Setup and Deployment Guide

To deploy your own version of Veritas News, follow these three parts carefully.

### **Part 1: Firebase Configuration**

First, you need to tell your Firebase project to trust your website URL.

1.  **Choose Your URL:** Your final GitHub Pages URL will be `https://your-username.github.io/your-repository-name/`. For this guide, we'll assume the repository name is `veritas-news`.
2.  **Authorize the Domain:**
      * Open the [**Firebase Console**](https://console.firebase.google.com/) and select your project.
      * Navigate to **Authentication** -\> **Settings** -\> **Authorized domains**.
      * Click **Add domain** and enter `your-username.github.io`.
      * Click **Add**. This whitelists your domain, allowing users to sign up and log in from your site.

### **Part 2: Gemini API Configuration**

Next, you need to get a secret API key and secure it so only your website can use it.

1.  **Get the API Key:**
      * Go to [**Google AI Studio**](https://aistudio.google.com/app/apikey) and click **Create API key**.
      * Copy the generated key.
2.  **Add Key to `index.html`:**
      * Open the `index.html` file.
      * Find the line `const apiKey = "";` (around line 430).
      * Paste your API key between the quotes: `const apiKey = "AIzaSy...your...key...";`.
      * Save the file.
3.  **Restrict the API Key (CRITICAL SECURITY STEP):**
      * Go to the [**Google Cloud Console Credentials page**](https://console.cloud.google.com/apis/credentials).
      * Click on the name of the API key you just created.
      * Under **Application restrictions**, select **Websites**.
      * Click **Add** and enter your GitHub Pages URL with a wildcard: `your-username.github.io/veritas-news/*`.
      * Click **Done**, then **Save**. This ensures no one else can use your key.

### **Part 3: Deploy to GitHub Pages**

With configuration complete, you're ready to publish.

1.  **Create a GitHub Repository:**
      * Go to GitHub and create a new **public** repository named `veritas-news`.
2.  **Upload the File:**
      * In the new repository, click **uploading an existing file**.
      * Drag and drop your saved `index.html` file into the upload area.
      * Click **Commit changes**.
3.  **Enable GitHub Pages:**
      * In the repository, go to **Settings** -\> **Pages**.
      * Under "Branch," select `main` (or `master`).
      * Click **Save**.

After a few minutes, your fully functional news aggregator will be live at: `https://your-username.github.io/veritas-news/`

