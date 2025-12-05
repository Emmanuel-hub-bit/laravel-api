A beginner-friendly Laravel application demonstrating routing, Blade templates, and basic MVC architecture. Built as part of the Moringa AI Capstone Project using AI-powered learning.
📋 Table of Contents

About the Project
Features
Prerequisites
Installation
Usage
Project Structure
Troubleshooting
Learning Resources
Contributing
License
Acknowledgments

🎯 About the Project
This project is a simple Laravel web application created to demonstrate:

Laravel routing fundamentals
Blade templating engine
Passing data from routes to views
Setting up a Laravel development environment on Windows with WSL2

Technology: Laravel 10.x (PHP Framework)
Development Environment:

Windows 11 with WSL2 (Ubuntu)
VS Code with Remote-WSL extension
PHP 8.3

Project Goal: Create a functional "Hello World" application that showcases Laravel's elegant syntax and MVC pattern.
✨ Features

✅ Custom route (/hello) with dynamic data
✅ Responsive Blade template with CSS styling
✅ No database required (file-based sessions)
✅ Clean, beginner-friendly code with comments
✅ Displays Laravel version and current timestamp
✅ Modern gradient UI design

🔧 Prerequisites
Before you begin, ensure you have the following installed:
Required Software

Windows 10/11 with WSL2 enabled
Ubuntu 20.04+ (WSL2 distribution)
PHP 8.1 or higher
Composer (PHP dependency manager)
VS Code (recommended) with Remote-WSL extension
Git (for version control)

Check Your Versions
bash# Check PHP version
php -v

# Check Composer version
composer --version

# Check WSL version
wsl -l -v
🚀 Installation
Follow these steps to get the project running on your local machine.
Step 1: Clone the Repository
bash# Navigate to your preferred directory
cd ~

# Clone the repository
git clone https://github.com/yourusername/laravel-hello-world.git

# Navigate into the project
cd laravel-hello-world
Step 2: Install Dependencies
bash# Install PHP dependencies via Composer
composer install
This will install all Laravel framework files and dependencies listed in composer.json.
Step 3: Set Up Environment File
bash# Copy the example environment file
cp .env.example .env

# Generate application encryption key
php artisan key:generate
Step 4: Configure Environment (Important!)
Open the .env file and ensure these settings:
envAPP_NAME="Laravel Hello World"
APP_ENV=local
APP_DEBUG=true
APP_URL=http://127.0.0.1:8000

# Session should be file-based (not database)
SESSION_DRIVER=file

# Cache can be file-based
CACHE_STORE=file

# Queue can be synchronous
QUEUE_CONNECTION=sync
Note: The DB_CONNECTION lines can be commented out since this project doesn't use a database.
Step 5: Clear Configuration Cache
bash# Clear any cached config
php artisan config:clear

# Clear application cache
php artisan cache:clear
Step 6: Set Proper Permissions
bash# Give write permissions to storage and cache directories
sudo chmod -R 775 storage bootstrap/cache
💻 Usage
Starting the Development Server
bash# Start Laravel's built-in development server
php artisan serve
Expected output:
INFO  Server running on [http://127.0.0.1:8000].

Press Ctrl+C to stop the server
Accessing the Application
Open your web browser and navigate to:

Default Laravel Welcome Page: http://127.0.0.1:8000
Custom Hello World Page: http://127.0.0.1:8000/hello

What You'll See
The /hello route displays:

A personalized greeting message
The Laravel framework version
Current date and time
Beautiful gradient background styling

Stopping the Server
Press Ctrl + C in your terminal to stop the development server.
📁 Project Structure
laravel-hello-world/
├── app/                          # Application core files
│   ├── Http/
│   │   └── Controllers/          # Controllers (empty for this project)
│   └── Models/                   # Eloquent models
├── bootstrap/                    # Framework bootstrap files
│   └── cache/                    # Framework cache
├── config/                       # Configuration files
├── database/                     # Database migrations and seeds
├── public/                       # Public assets (entry point)
│   └── index.php                 # Application entry point
├── resources/                    # Views and raw assets
│   └── views/
│       ├── welcome.blade.php     # Default Laravel page
│       └── hello.blade.php       # Custom Hello World page ⭐
├── routes/                       # Application routes
│   └── web.php                   # Web routes (includes /hello) ⭐
├── storage/                      # Storage for logs, cache, sessions
│   ├── app/
│   ├── framework/
│   │   └── sessions/             # Session files
│   └── logs/
├── tests/                        # Automated tests
├── vendor/                       # Composer dependencies
├── .env                          # Environment configuration
├── .env.example                  # Example environment file
├── artisan                       # Laravel CLI tool
├── composer.json                 # PHP dependencies
├── composer.lock                 # Locked dependency versions
└── README.md                     # This file
Key Files Modified for This Project:

⭐ routes/web.php - Added custom /hello route
⭐ resources/views/hello.blade.php - Created custom view with styling

🔍 Code Walkthrough
Custom Route (routes/web.php)
phpRoute::get('/hello', function () {
    $data = [
        'name' => 'Laravel Developer',
        'framework' => 'Laravel',
        'version' => app()->version()
    ];
    
    return view('hello', $data);
});
What it does:

Creates a route that responds to GET requests at /hello
Prepares data array with name, framework, and version
Passes data to the hello Blade view

Blade Template (resources/views/hello.blade.php)
The view uses Blade syntax ({{ }}) to display dynamic data:

{{ $name }} - Displays the name from route
{{ $framework }} - Displays framework name
{{ $version }} - Displays Laravel version
{{ date('F j, Y, g:i a') }} - Displays current timestamp

🐛 Troubleshooting
Issue 1: Missing Application Key
Error:
No application encryption key has been specified.
Solution:
bashphp artisan key:generate
php artisan config:clear
php artisan serve

Issue 2: Incorrect Cipher/Key Length
Error:
Unsupported cipher or incorrect key length.
Solution:
bash# Edit .env and clear APP_KEY line
nano .env  # Set: APP_KEY=

# Regenerate key
php artisan key:generate
php artisan config:clear
php artisan serve

Issue 3: Database File Not Found
Error:
Database file at path [.../database.sqlite] does not exist.
Solution:
Edit .env file and change:
envSESSION_DRIVER=file
Then:
bashphp artisan config:clear
php artisan serve

Issue 4: Permission Denied (Storage)
Error:
failed to open stream: Permission denied
Solution:
bashsudo chmod -R 775 storage bootstrap/cache

Issue 5: Composer Install Fails (Memory)
Error:
Fatal error: Allowed memory size exhausted
Solution:
bashphp -d memory_limit=-1 /usr/local/bin/composer install

Issue 6: VS Code Can't Connect to WSL
Solution:

Install "Remote - WSL" extension in VS Code
Ensure WSL2 is running: wsl -l -v
From WSL terminal: code .

📚 Learning Resources
Official Documentation

Laravel 10.x Documentation
Laravel Routing
Blade Templates
Laravel Installation

Video Tutorials

Laravel Crash Course - Traversy Media
Laravel From Scratch - Laracasts

Community Resources

Laravel Reddit
Laracasts Forum
Stack Overflow - Laravel Tag

Development Tools

Laravel Artisan Cheatsheet
Laravel News

🤝 Contributing
This is a learning project, but contributions are welcome!

Fork the repository
Create your feature branch (git checkout -b feature/AmazingFeature)
Commit your changes (git commit -m 'Add some AmazingFeature')
Push to the branch (git push origin feature/AmazingFeature)
Open a Pull Request

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
🙏 Acknowledgments

Moringa School - For the AI Capstone Project curriculum
Laravel Community - For excellent documentation
Taylor Otwell - Creator of Laravel
Claude AI - For assisting with learning and troubleshooting
WSL Team - For making Linux development on Windows seamless

👤 Author
Your Name

GitHub: @yourusername
Project: Moringa AI Capstone - Laravel Toolkit

🚀 Next Steps
After completing this project, consider:

Adding database functionality with Eloquent ORM
Building a simple CRUD application
Implementing Laravel authentication
Creating RESTful API endpoints
Deploying to production (Railway, Heroku, DigitalOcean)


Built with ❤️ using Laravel and AI-powered learning
Last Updated: December 2025
