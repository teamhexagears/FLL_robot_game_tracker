# FLL Robot Game Tracker

The FLL Bioglow Results Tracker helps teams record mission results and scores during a robot game run. It includes a 2:30 mission timer and saves run results to a Google Sheet. With the results, we can do statistics on our performance

## Table of Contents
* [Initial Setup](#initial-setup)
* [Customize the app for your team](#how-to-customize-the-app-for-your-team)
* [Future Roadmap](#future-roadmap)


# Initial Setup
At this moment, some of the steps are manual.
Follow these steps to set up and run the app.

## 1. Fork and clone the repository

1. Go to the [repository fork page](https://github.com/teamhexagears/FLL_robot_game_tracker/fork).
2. Clone your fork to your computer.
  - If you don't know how to use Github, you can download the ZIP file directly(see [screenshot](screenshots/download_repo.png))
## 2. Import the database into Google Sheets

1. Login to your google account and open [Google Sheets](https://docs.google.com/spreadsheets/u/0/).
2. Create a new **Blank Spreadsheet**.
3. Select **File > Import > Upload**.
4. Choose `backend\FLL Robot Game Tracker Database.xlsx` from your cloned repository.

## 3. Add the Apps Script files

1. In your spreadsheet, select **Extensions > Apps Script**.
2. In the Apps Script window, create two files as "Scripts", if they do not already exist (see [screenshot](screenshots/add_file.png)).:
   - `Code.gs`
   - `webapp.gs`
3. You can find Code.gs and webapp.gs under [backend](backend/) directory, copy the file contents over to Google App Script
4. Press Ctrl + s on each file to save

## 4. Set up the tracker

1. In Apps Script, open `Code.gs` and select `setupTrackerSheet`. (see [screenshot](screenshots/setup_tracker.png))
2. Click **Run**. 
3. If prompted to authorize access, click **Review permissions**, then **Advanced**(see [screenshot](screenshots/trust_app.png)), then  click on **Go to untitled project (unsafe)** (see [screenshot](screenshots/trust_app2.png)).
4. Scroll down and press **Continue**

## 5. Deploy the web app

1. In Google Apps Script, click on **Deploy > New deployment**. (see [screenshot](screenshots/deploy.png)).
2. Select **Web app**. (see [screenshot](screenshots/new_deployment.png)).
3. Under **Who has access** dropdown menu, click **Anyone**.
3. Click **Deploy**.
4. Copy the web app URL and store it somewhere for later use.

## 6. Configure the frontend

1. Duplicate `frontend/app.js.template` and reanme to `frontend/app.js`.
Confirm the file extension change if your computer prompts you for it.
2. Open `frontend/app.js` in a text editor.
3. Paste the copied URL on line 83. It should look like this:

   ```js
   const appConfig = {
     apiUrl: 'https://script.google.com/macros/s/xxxx/exec'
   }
   ```
4. Save the file

> [!CAUTION]
> Do not share your `apiUrl`. The deployment is configured so anyone with the URL can access the spreadsheet. The `frontend/app.js` file is listed in `.gitignore` so the URL is not committed.

## 7. Run the app

Open `frontend/index.html` in your browser.

If you are not sure how to do that, you can try
- Locating your file from your Folder, then drag and drop it to your web browser
- or go to **File** > **Open** on your web browser, and navigate tto your frontend/index.html

## 8. ENJOY!!!!!!!!!!!!!!!


# How to customize the app for your team

## Update Database
The database is the Google Sheets you imported in Step 2 during initial setup
It has two tabs by default, Results and Missions

- You usually don't need to touch the Results tab, as it is maintained by frontend script
- For Missions tab
  - All the missions for Bioglow has already been populated, for future seasons you'll have to populate the missions table. Feel free to submit a pull-request if you have done it.
  - You will need to update the **Run number** column in the Mission tab, as each team plan the routes differently. (see [screenshot](screenshots/change_run_number.png))
  - Once Missions have been modified and saved, refresh index.html on your browser directly and it will take effect.
  - You can also modified the **Mission Name** to use your own wording (see [screenshot](screenshots/change_mission_name.png))

## Make changes to Google App Scripts
It's possible that you want to do a bugfix or add more features in Google App Script
Make sure following actions have been done
1. Re-deploy the Google App Script mentioned in [Step 5](#5-deploy-the-web-app)
2. Update frontend/app.js following instructions in [Step 6](6-configure-the-frontend)



# Future Roadmap 
Feel free to contribute by submitting pull-requests!

## Simplify Initial Setup phase

### Goals
- Reduce manual steps during initial setup phase

## Statistical Page

Provide a page that analyzes saved robot-game runs by mission, run number, attempt, score, completion time, and success rate.

### Goals

- Let teams identify reliable missions, unreliable missions, slow missions, and trends across practice attempts.
- Use the existing `Results` sheet as the source of truth.

### Metrics

The page must provide at least:

| Metric | Definition |
|---|---|
| Mission success rate | Successful results divided by recorded results for that mission |
| Average mission score | Mean of the mission scores for one mission across recorded attempts |
| Run success rate | Successful results divided by recorded results for each run |
| Average time per run | Mean measured interval between each run |
| Average run score | Average score of each run |
| Score per second each run | Score per second can show us which run has most value |
