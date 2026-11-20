# FLL Robot Game Tracker

The FLL Bioglow Results Tracker helps teams record mission results and scores during a robot game run. It includes a 2:30 mission timer and saves run results to a Google Sheet. With the results, we can do statistics on our performance

At this moment, some of the steps are manual.
Follow these steps to set up and run the app.

## 1. Fork and clone the repository

1. Go to the [repository fork page](https://github.com/teamhexagears/FLL_robot_game_tracker/fork).
2. Clone your fork to your computer.

## 2. Import the database into Google Sheets

1. Login to your google account and open [Google Sheets](https://docs.google.com/spreadsheets/u/0/).
2. Create a new spreadsheet.
3. Select **File > Import > Upload**.
4. Choose `backend\FLL Bioglow Results.xlsx` from your cloned repository.

## 3. Add the Apps Script files

1. In your spreadsheet, select **Extensions > Apps Script**.
2. In the Apps Script window, create two files:
   - `Code.gs`
   - `webapp.gs`
3. You can find Code.gs and webapp.gs under [backend](backend/) directory, copy the file contents over to Google App Script

## 4. Set up the tracker

1. In Apps Script, open `Code.gs` and select `setupTrackerSheet`. (see [screenshot](screenshots/setup_tracker.png))
2. Click **Run**. 
3. If prompted to authorize access, click **Review permissions**, then **Advanced**(see [screenshot](screenshots/trust_app.png)), then **Go to untitled project (unsafe)** (see [screenshot](screenshots/trust_app2.png)).

## 5. Deploy the web app

1. In Google Apps Script, click on **Deploy > New deployment**. (located at top right corner)
2. Select **Web app**. (see [screenshot](screenshots/new_deployment.png)).
3. Under **Who has access** dropdown menu, click **Anyone**.
3. Click **Deploy**.
4. Copy the web app URL.

## 6. Configure the frontend

1. Copy `frontend/app.js.template` to `frontend/app.js`.
2. Open `frontend/app.js` in a text editor.
3. Paste the copied URL on line 83. It should look like this:

   ```js
   const appConfig = {
     apiUrl: 'https://script.google.com/macros/s/xxxx/exec'
   }
   ```
   > [!CAUTION]
   > Do not share your `apiUrl`. The deployment is configured so anyone with the URL can access the spreadsheet. The `frontend/app.js` file is listed in `.gitignore` so the URL is not committed.

## 7. Run the app

Open `frontend/index.html` in your browser.

## 8. ENJOY!!!!!!!!!!!!!!!