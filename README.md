# Download Multiple Google Drive Files

This is a simple web application served by an Express server that lets users download multiple Google Drive files by pasting one or more file links or IDs. It supports two download modes: downloading files individually or bundling them into a ZIP archive. The app uses the new Google Identity Services (GIS) for authentication, JSZip for creating ZIP archives, and Tailwind CSS for styling (I kinda imported the whole thing because I was lazy).

## Features

- **Google Authentication:** Uses GIS to obtain an access token and caches it (via localStorage) so the user doesn't have to sign in every time.
- **Multiple Download Modes:**
  - **Individual Downloads:** Downloads each file separately (multiple browser prompts).
  - **ZIP Download:** Combines all files into a single ZIP archive with a two-phase progress bar.
- **Progress Tracking:** Displays download and zipping progress in a visual progress bar — which could be better but works.

## Live Demo

A live instance of this application is available at:  
[https://web-drive-production.up.railway.app/](https://web-drive-production.up.railway.app/)

## Prerequisites (to make your own)

- A Google Cloud Console project with the [Google Drive API](https://console.cloud.google.com/) enabled.
- An OAuth 2.0 Client ID. Replace `YOUR_CLIENT_ID.apps.googleusercontent.com` in the code with your actual client ID.
- [Node.js](https://nodejs.org/) installed on your system.

## Setup

1. **Clone or Download the Repository:**  
   Download the source code or clone the repository to your local machine.

2. **Configure Your Client ID:**  
   Open the main HTML file (e.g., `index.html`) in your text editor and replace:
   ```js
   const CLIENT_ID = 'YOUR_CLIENT_ID.apps.googleusercontent.com';
   ```
   with your actual OAuth 2.0 Client ID from the Google Cloud Console.

3. **Install Dependencies and Run the Server:**  
   This project is served by an Express server. In the project directory, run the following commands:
   ```bash
   npm install
   npm run start
   ```
   This will install all necessary dependencies and start the server. The Express server is configured to serve the HTML page at every path.

4. **Open the Application:**  
   Open your browser and navigate to `http://localhost:3000` (or the appropriate port if changed).

## Usage

1. **Sign In:**  
   - If not already signed in, click the **Sign In & Get Token** button (blue).  
   - Once authenticated, the token status will display "Access token is available", the **Sign In** button will be hidden, and a red **Logout** button will appear.

2. **Paste File Links or IDs:**  
   - Enter one or more Google Drive file links or IDs (one per line) in the provided textarea.

3. **Select Download Mode:**  
   - Choose either "Individual Downloads" (multiple prompts) or "Download as ZIP" (single prompt with progress tracking).

4. **Download Files:**  
   - Click the **Download Files** button.  
   - In ZIP mode, a progress bar will indicate the status during file downloads and while the files are being zipped.

5. **Logout:**  
   - Click the **Logout** button (red) to clear the token and disable downloads until re-authentication.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

- [Google Identity Services](https://developers.google.com/identity/gsi/web)
- [JSZip](https://stuk.github.io/jszip/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Express](https://expressjs.com/)
