# FLL Robot Game Tracker

The FLL Bioglow Results Tracker helps teams record mission results and scores during a robot game run. It includes a 2:30 mission timer and saves run results to a Google Sheet. With the results, we can do statistics on our performance

At this moment, some of the steps are manual.
Follow these steps to set up and run the app.

## 1. Fork and clone the repository

1. Go to the [repository fork page](https://github.com/teamhexagears/FLL_robot_game_tracker/fork).
2. Clone your fork to your computer.

## 2. Import the database into Google Sheets

1. Open [Google Sheets](https://docs.google.com/spreadsheets/u/0/).
2. Create a new spreadsheet.
3. Select **File > Import > Upload**.
4. Choose `backend\FLL Bioglow Results.xlsx` from your cloned repository.

## 3. Add the Apps Script files

1. In your spreadsheet, select **Extensions > Apps Script**.
2. In the Apps Script window, create three files:
   - `appscript.json`
   - `Code.gs`
   - `webapp.gs`
3. Copy the contents of the corresponding files from the repository's `backend` directory into the Apps Script files.

## 4. Set up the tracker

1. In Apps Script, open `Code.gs` and select `setupTrackerSheet`.
2. Click **Run**.
3. If prompted to authorize access, click **Review permissions**, then **Advanced > Go to untitled project (unsafe)**.

## 5. Deploy the web app

1. In Apps Script, click **Deploy > New deployment**.
2. Select **Web app**.
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

## 7. Run the app

Open `frontend/index.html` in your browser.

## 8. ENJOY!!!!!!!!!!!!!!!