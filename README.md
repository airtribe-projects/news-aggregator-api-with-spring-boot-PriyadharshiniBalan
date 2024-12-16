**News Aggregator API - README**

**Overview**

The News Aggregator API is a Spring Boot application that provides user authentication and personalized news aggregation based on user preferences. It supports user registration, login, and interaction with external news APIs to fetch articles tailored to user interests. The application leverages JWT-based authentication, in-memory databases for user data, and Spring Security for access control.

**Features**
1) User Authentication and Authorization
   
    JWT-based token authentication.
    Secure user registration and login endpoints.

2) User Preferences
   
    Retrieve and update personalized news preferences.

3) News Fetching
   
    Fetch news articles based on user preferences from external APIs.
    Optionally cache news articles to reduce external API calls.

4) Article Management
 
    Mark articles as "read" or "favorite."
    Retrieve lists of read and favorite articles.

5) Error Handling
   
    Comprehensive exception handling for invalid requests, authentication errors, and authorization failures.

**Endpoints**

**Authentication**

  POST /api/register: Register a new user.

  Request Body:
  {
      "username": "example",
      "password": "password123"
  }
  
  POST /api/login: Log in an existing user.

  Request Body:
  {
      "username": "example",
      "password": "password123"
  }

**Preferences**

  GET /api/preferences: Retrieve the logged-in user's news preferences.
  PUT /api/preferences: Update the logged-in user's news preferences.
  
  Request Body:
  {
      "categories": ["technology", "science"],
      "sources": ["bbc-news", "cnn"]
  }

**News**

  GET /api/news: Fetch news articles based on user preferences.

**Article Management**

  POST /api/news/{id}/read: Mark a news article as read.
  POST /api/news/{id}/favorite: Mark a news article as favorite.
  GET /api/news/read: Retrieve all read articles.
  GET /api/news/favorites: Retrieve all favorite articles.

**Setup**

**Requirements**

  Java 17 or later
  Maven or Gradle
  API Key for external news services (e.g., NewsAPI, GNews API)

**Steps**

1) Clone the repository:
   
  git clone https://github.com/your-repo/news-aggregator-api.git
  cd news-aggregator-api

2) Configure API keys for external news services:
   
  Add your API keys in application.properties or as environment variables:

  newsapi.key=your_api_key
  gnews.key=your_api_key

3) Build the project:
   
  ./mvnw clean install

4) Run the application:
   
  ./mvnw spring-boot:run

**Technologies Used**

  Spring Boot: Core framework.
  Spring Security: Authentication and authorization.
  JWT: Token-based authentication.
  H2 Database: In-memory database for storing user data.
  Spring Web: RESTful API implementation.
  WebClient: Asynchronous HTTP requests to external APIs.
  Validation: Input validation using @Valid and Hibernate Validator.

**Testing**
  Use Postman  or cURL to test endpoints.
  Example login test with cURL:
    curl -X POST http://localhost:8080/api/login -H "Content-Type: application/json" -d '{"username":"example","password":"password123"}'
