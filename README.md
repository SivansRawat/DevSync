# DevSync
DevSync: Real-time collaborative development environment with an AI assistant. Build, chat, and run code in the browser with MERN, Socket.IO, and Google Gemini.



## Setup and Installation

### Prerequisites

Before you begin, ensure you have the following installed on your system:

* **Node.js & npm:**
    * Download and install from [nodejs.org](https://nodejs.org/).
    * Verify installation: `node -v` and `npm -v`
* **MongoDB:**
    * **Recommended (Cloud):** Create a free-tier cluster on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas). This is easier for setup and management. Follow their guide to create a cluster, set up a database user, and whitelist your IP address.
    * **Local Installation:** Download and install MongoDB Community Server from [mongodb.com/try/download/community](https://www.mongodb.com/try/download/community) if you prefer to run it locally.
* **Redis:**
    * **Recommended (Cloud):** Use a free tier from [Redis Cloud](https://redis.com/try-free/).
    * **Local Installation:** Download and install Redis from [redis.io/download](https://redis.io/download) if you prefer to run it locally.
* **Google Gemini API Key:**
    * Obtain an API key from [Google AI Studio](https://aistudio.google.com/app/apikey) or the Google Cloud console.

### Backend Setup

1.  **Clone the repository:**
    ```bash
    git clone <repository_url>
    cd DevSync/backend
    ```
    *(Replace `<repository_url>` with the actual URL of your project's GitHub repo)*

2.  **Install dependencies:**
    ```bash
    npm install
    # or if you use yarn:
    yarn install
    ```

3.  **Create `.env` file:**
    * Create a file named `.env` in the `backend/` directory.
    * Copy the contents from `.env.example` into your new `.env` file.
    * Fill in the placeholder values with your actual credentials:

        ```dotenv
        # Server Port
        PORT=3000

        # MongoDB Connection URI (from MongoDB Atlas or local)
        # Example Atlas: mongodb+srv://<username>:<password>@cluster0.abcde.mongodb.net/devsync_db?retryWrites=true&w=majority
        # Example Local: mongodb://localhost:27017/devsync_db
        MONGODB_URI="your_mongodb_atlas_or_local_uri_here"

        # JWT Secret Key (Generate a strong, random string)
        JWT_SECRET="a_very_secret_and_long_random_string_for_jwt_signing"

        # Redis Configuration (from Redis Cloud or local)
        # Example Redis Cloud:
        REDIS_HOST="your_redis_cloud_host"
        REDIS_PORT="your_redis_cloud_port"
        REDIS_PASSWORD="your_redis_cloud_password"
        # OR if your Redis client supports a full URL (often preferred for Redis Cloud):
        # REDIS_URL="redis://default:your_redis_cloud_password@your_redis_cloud_host:your_redis_cloud_port"
        # Example Local Redis:
        # REDIS_HOST=localhost
        # REDIS_PORT=6379
        # REDIS_PASSWORD=

        # Google Generative AI Key
        GOOGLE_AI_KEY="your_google_gemini_api_key_here"
        ```
    * **Important:** Add `.env` to your `.gitignore` file to prevent it from being committed to version control.

### Frontend Setup

1.  **Navigate to the frontend directory:**
    ```bash
    cd ../frontend
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    # or if you use yarn:
    yarn install
    ```

3.  **Create `.env` file:**
    * Create a file named `.env` in the `frontend/` directory.
    * Add the following line, ensuring the port matches your backend `PORT`:

        ```dotenv
        VITE_API_URL=http://localhost:3000
        ```
    * **Important:** Add `.env` to your `.gitignore` file to prevent it from being committed to version control.

## Running the Application

1.  **Start the Backend Server:**
    * Open your first terminal window.
    * Navigate to the `backend/` directory.
    * Run:
        ```bash
        node server.js
        # Or if you have a start script: npm start
        ```
    * You should see console messages indicating successful connection to MongoDB and Redis, and that the server is running on the specified port.

2.  **Start the Frontend Development Server:**
    * Open your second terminal window.
    * Navigate to the `frontend/` directory.
    * Run:
        ```bash
        npm run dev
        # Or if you use yarn: yarn dev
        ```
    * This will start the React development server. It will usually provide a local URL (e.g., `http://localhost:5173`) in the console.

3.  **Access the Application:**
    * Open your web browser and navigate to the URL provided by the frontend development server.
    * You can now register a new user, log in, create projects, and start using the collaborative features and AI assistant!

## AI Capabilities

To interact with the AI assistant in a project's chat:
* Type `@ai` followed by your prompt (e.g., `@ai create a basic express server`).
* The AI will generate code and file structures in response, which will then be mounted to the WebContainer in your browser.
* Use the "run" button in the project view to execute the AI-generated code.

## Contributing

(Optional section - if you plan to open source or have others contribute)
Contributions are welcome! Please follow these steps:
1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature-name`).
3.  Make your changes.
4.  Commit your changes (`git commit -m 'feat: Add new feature'`).
5.  Push to the branch (`git push origin feature/your-feature-name`).
6.  Open a Pull Request.

## License

(Optional section - choose a license, e.g., MIT, Apache 2.0)
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
