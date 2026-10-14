# MindMath

Mental addition and subtraction trainer, plus squares, cubes and roots. It runs as an installable app on your phone, so you do not need Android Studio.

## Put it online (free, about 3 minutes)
1. Create a new public repository on GitHub.
2. Upload all the files (index.html, sw.js, manifest.webmanifest, icons, README.md) to the repository root.
3. Go to Settings > Pages. Under "Build and deployment" choose "Deploy from a branch", branch `main`, folder `/ (root)`, then Save.
4. After a minute your app is live at `https://YOUR-USERNAME.github.io/REPO-NAME/`.

## Install on your phone
Open that link in Chrome on Android, tap the menu (three dots), then "Install app" or "Add to Home screen".

## Practice reminders (works even when the app is killed)
The phone cannot wake a closed web app by itself, so a tiny free server sends the alert instead (Web Push).
1. Sign up free at cloudflare.com. Open Workers & Pages > Create > Worker. Name it `mindmath`, Deploy, then Edit code.
2. Delete the sample code, paste the whole of `worker.js`, and Deploy.
3. Storage & Databases > KV > Create a namespace called `mindmath`.
4. Open your Worker > Settings > Bindings > Add > KV namespace. Variable name must be exactly `MM`, pick the namespace, Save.
5. Worker > Settings > Triggers > Cron Triggers > Add: `*/5 * * * *`
6. Optional but recommended: Settings > Variables > add `ALLOW_ORIGIN` = `https://YOUR-USERNAME.github.io`
7. Copy your Worker address (like `https://mindmath.yourname.workers.dev`). In `index.html` paste it into `const PUSH_URL='';`, then upload `index.html` and `sw.js` to GitHub again.
8. Open the app, pull down to refresh, turn on "Practice reminders", allow notifications, and tap "Send a test alert".

## Make it LOUD on Android
A website cannot choose its own sound, Android decides. Long-press the MindMath icon > App info > Notifications, then set the category to "Urgent / Make sound and pop on screen" and pick an alarm-style sound. Also set Battery to "Unrestricted". Do not use "Force stop", it blocks all notifications until you open the app again.

## Notes
- Your history is stored on your phone only. Clearing Chrome's site data erases it.
- The app picks questions using the digits, carries and borrows you get wrong or answer slowly.
