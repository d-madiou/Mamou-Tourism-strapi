# Mamou Tourism - Strapi Backend
[![Ask DeepWiki](https://devin.ai/assets/askdeepwiki.png)](https://deepwiki.com/d-madiou/Mamou-Tourism-strapi)

This repository contains the Strapi backend for the Mamou Tourism and City Information website. It serves as a headless Content Management System (CMS) to manage all dynamic content for the platform, including news, events, local services, and tourist information for the Mamou region of Guinea.

## ✨ Features

This Strapi application is configured with a rich set of content types to manage various aspects of the city's data:

*   **General Information:** About pages and Diwal (regional) information.
*   **News & Events:** Manage blog articles (`articles-actualitee`), events, and sports news.
*   **Tourism & Hospitality:** Curate lists of hotels, restaurants, and places to visit (`lieux-a-visiter`).
*   **Civic Information:** Details on elected officials (`elus-officiel`), administrative documents, sub-prefectures (`sous-prefecture`), and police stations (`postes-police`).
*   **Education:** Manage school listings and educational statistics.
*   **Community:** Information on popular activities, photo galleries, and sports matches.
*   **Media Management:** A gallery system to categorize and display images for various sections like culture, sports, and tourism.

## 🚀 Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

*   Node.js (v18 to v22)
*   `npm` or `yarn`

### Installation & Setup

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/d-madiou/Mamou-Tourism-strapi.git
    cd Mamou-Tourism-strapi
    ```

2.  **Install dependencies:**
    ```sh
    npm install
    ```
    or
    ```sh
    yarn install
    ```

3.  **Set up environment variables:**
    Create a `.env` file in the root directory by copying the example file:
    ```sh
    cp .env.example .env
    ```
    Populate the `.env` file with your configuration. You must generate your own secret keys for security.

    ```dotenv
    # .env
    HOST=0.0.0.0
    PORT=1337
    
    # Generate these using 'openssl rand -base64 32' or similar
    APP_KEYS="key1,key2,key3,key4"
    API_TOKEN_SALT=your_generated_salt_here
    ADMIN_JWT_SECRET=your_generated_admin_secret_here
    JWT_SECRET=your_generated_content_api_secret_here
    TRANSFER_TOKEN_SALT=your_generated_transfer_salt_here
    ENCRYPTION_KEY=tobemodified

    # Database (SQLite is default, for PostgreSQL uncomment and configure)
    # DATABASE_CLIENT=postgres
    # DATABASE_HOST=127.0.0.1
    # DATABASE_PORT=5432
    # DATABASE_NAME=strapi-db
    # DATABASE_USERNAME=strapi-user
    # DATABASE_PASSWORD=strapi-password
    # DATABASE_SSL=false
    ```
    The project uses SQLite by default, which requires no extra configuration. For production, it is recommended to switch to PostgreSQL by updating the variables in your `.env` file.

### Available Scripts

*   **Run in development mode:**
    Starts the application with auto-reload enabled.
    ```sh
    npm run develop
    ```

*   **Build the admin panel:**
    Builds the admin UI for production.
    ```sh
    npm run build
    ```

*   **Run in production mode:**
    Starts the application with auto-reload disabled. Make sure you have run the `build` script first.
    ```sh
    npm run start
    ```

## ⚙️ Content Types

The application manages the following content types:

*   `about`: General information pages.
*   `activite-populaire`: Popular activities categorized by type (sport, commerce, etc.).
*   `articles-actualitee` (Blog): News articles with categories like education, sports, and politics.
*   `diwal`: Specific cultural or regional pages with text and photos.
*   `document-administratif`: Information on obtaining official documents (birth certificates, permits).
*   `ecole`: Directory of schools (primary, college, university).
*   `education-statistique`: Yearly statistics on education.
*   `elus-officiel`: Profiles of elected and official figures.
*   `event`: Upcoming events with details on date, location, and type.
*   `gallerie`: Photo gallery with categories (Culture, Sport, Tourism).
*   `hotel`: Directory of hotels, motels, and lodges.
*   `lieux-a-visiter`: Tourist attractions and points of interest.
*   `matchs-sportif`: Details on scheduled and past sports matches.
*   `postes-police`: List of police and gendarmerie stations.
*   `restaurant`: Directory of restaurants categorized by cuisine type.
*   `sous-prefecture`: Information about the region's sub-prefectures.
*   `sportnew`: News specific to sports.

## 🚢 Deployment

This repository includes a GitHub Actions workflow in `.github/workflows/deploy.yml` for automated deployment to a VPS.

*   **Trigger:** Pushing to the `main` branch.
*   **Process:** The workflow connects to a server via SSH, pulls the latest changes from the `main` branch, installs dependencies, builds the Strapi application, and restarts it using `pm2`.
*   **Setup:** To use this workflow, you need to configure the following secrets in your GitHub repository settings:
    *   `VPS_HOST`: The IP address or hostname of your server.
    *   `VPS_USERNAME`: The username for the SSH connection.
    *   `VPS_SSH_KEY`: The private SSH key to access the server.
