🎬 Movie App

Welcome to the Movie App! 🌟 This app allows users to browse a collection of movies, like their favorite ones, and store them in a database using Appwrite. The app fetches data from an external movie API, and users can view their liked movies anytime.

🚀 Features

Browse Movies: View a curated list of movies fetched from an external API. 🍿

Like Movies: Mark your favorite movies to store them in Appwrite. ❤️

View Liked Movies: Access your favorite movies anytime. 📱

User Authentication: Secure sign-in and session management through Appwrite. 🔐

🛠️ Tech Stack

Frontend: React.js or Vanilla JS, HTML, CSS 🎨

Backend: Appwrite (for data storage and user authentication) 🗃️

API: External Movie API (e.g., TMDB, OMDB) 🌐

Database: Appwrite (stores liked movies) 🛠️

📋 Prerequisites

Before getting started, make sure you have the following:

Node.js installed for frontend development ⚙️

Appwrite account and instance set up 💻

API Key for an external movie API (e.g., TMDB, OMDB) 🎥

Appwrite SDK installed in your project 📚

📝 Installation

1️⃣ Clone the repository:

git clone https://github.com/yourusername/movie-app.git
cd movie-app

2️⃣ Install dependencies:

npm install

3️⃣ Set up Appwrite:

Create an Appwrite project and note down the API endpoint and Project ID. 🔑

Set up your Appwrite database and create a collection to store liked movies.

Collection fields:

movieId: String (unique identifier from the API)

movieTitle: String

moviePoster: String (URL of the movie poster)

userId: String (user identifier, for user-specific liked movies)

4️⃣ Configure Appwrite SDK:

In the app’s configuration file (config.js), update the Appwrite API endpoint and Project ID, and set the external movie API key.

export const config = {
  appwriteEndpoint: 'https://[APPWRITE-ENDPOINT]',
  projectId: '[PROJECT-ID]',
  apiKey: '[MOVIE-API-KEY]',
};

5️⃣ Start the development server:

npm start

Visit http://localhost:3000 to view the app. 🎉

🎬 Usage

Browse Movies: The home page fetches a list of popular movies from the external API and displays them for you to explore. 🌟

Like Movies: Click the "Like" ❤️ button on any movie you want to save to your list of liked movies.

View Liked Movies: Navigate to the "Liked Movies" section to see all the movies you’ve liked! 🎥

Authentication: Log in to Appwrite to track your liked movies and ensure your preferences are stored securely. 🔐

📡 API Integration

The movie data is fetched from the external movie API. Here’s an example of how the data can be fetched from the TMDB API:

const fetchMovies = async () => {
  const response = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}`);
  const data = await response.json();
  return data.results;
};

💾 Storing Liked Movies in Appwrite

When a user likes a movie, the app sends the movie details to the Appwrite database:

const addLikedMovie = async (movie) => {
  const user = await sdk.account.get(); // Get current user
  const likedMovie = {
    userId: user.$id,
    movieId: movie.id,
    movieTitle: movie.title,
    moviePoster: movie.poster_path,
  };

  const response = await sdk.database.createDocument(
    'liked_movies_collection', // Collection name
    likedMovie
  );

  return response;
};

💡 Additional Features (Optional)

Search Functionality: Add a search bar to find specific movies based on title or genre. 🔍

Recommendations: Show recommended movies based on the user's liked movies. 🎯

Happy Coding! 🎥🚀

