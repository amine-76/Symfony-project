# Yu-Gi-Oh! Card Management System

A comprehensive web application built with Symfony 6.4 for managing Yu-Gi-Oh! trading cards, their editions, and supported languages. This system provides full CRUD (Create, Read, Update, Delete) functionality for card collections with a modern, responsive interface using Bulma CSS framework.

## Features

- **Card Management**: Complete CRUD operations for Yu-Gi-Oh! cards including:
  - Card name, category (Monster, Magic, Trap)
  - Attributes (Fire, Water, Earth, etc.)
  - Level, ATK/DEF statistics
  - Type, specificity, and detailed descriptions
  - Card images
- **Edition Management**: Track card editions with release dates
- **Language Support**: Multi-language card support
- **Pagination**: Efficient browsing with KnpPaginatorBundle
- **Responsive Design**: Modern UI with Bulma CSS framework
- **Form Management**: User-friendly forms for data entry and editing

## Technologies Used

- **PHP 8.1+**
- **Symfony 6.4** - Web framework
- **Doctrine ORM 3.1** - Database abstraction layer
- **PostgreSQL** - Primary database
- **Twig 3.x** - Templating engine
- **Bulma CSS** - UI framework
- **KnpPaginatorBundle** - Pagination
- **Docker & Docker Compose** - Containerization
- **Stimulus & Turbo** - Frontend enhancements

## Requirements

- PHP 8.1 or higher
- Composer
- Docker and Docker Compose (for database)
- PostgreSQL (if not using Docker)

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/amine-76/Symfony-project.git
cd Symfony-project
```

### 2. Install PHP dependencies
```bash
composer install
```

### 3. Set up the database with Docker
```bash
# Start the PostgreSQL database container
docker-compose up -d

# Wait a few seconds for the database to initialize, then create the database schema
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
```

### 4. Load sample data (optional)
```bash
# Import the provided SQL data
psql -h localhost -p 5432 -U app -d app < P12_yugioh.psql.sql
```

### 5. Install frontend assets
```bash
php bin/console importmap:install
```

### 6. Start the Symfony development server
```bash
symfony serve -d
# Or alternatively:
php -S localhost:8000 -t public/
```

The application will be available at `http://localhost:8000`.

## Usage

### Available Routes

The application provides the following main functionalities:

#### Homepage
- **GET `/accueil`** - Welcome page with project information

#### Card Management
- **GET `/carte`** - Browse all cards with pagination
- **GET `/carte/insert`** - Form to add a new card
- **POST `/carte/insert`** - Submit new card data
- **GET `/carte/{id}`** - View detailed card information
- **GET `/carte/{id}/update`** - Form to edit existing card
- **POST `/carte/{id}/update`** - Submit card updates
- **GET `/carte/{id}/delete`** - Delete a card

#### Edition Management
- **GET `/edition`** - Browse all editions with pagination
- **GET `/edition/insert`** - Form to add a new edition
- **POST `/edition/insert`** - Submit new edition data
- **GET `/edition/{id}`** - View edition details
- **GET `/edition/{id}/update`** - Form to edit existing edition
- **GET `/edition/{id}/delete`** - Delete an edition

#### Language Management
- **GET `/langue`** - Browse all supported languages
- **GET `/langue/insert`** - Form to add a new language
- **POST `/langue/insert`** - Submit new language data
- **GET `/langue/{id}`** - View language details
- **GET `/langue/{id}/update`** - Form to edit existing language
- **GET `/langue/{id}/delete`** - Delete a language

### Navigation

The application features a clean navigation bar with:
- **Cartes** - Card management section
- **Editions** - Edition management section  
- **Langues** - Language management section

### Data Model

The application manages three main entities:

1. **Carte (Card)**
   - Basic information (name, category, image)
   - Game statistics (level, ATK, DEF)
   - Descriptive data (type, attribute, description)

2. **Edition**
   - Edition name and release date
   - Relationships with cards

3. **Langue (Language)**
   - Language names for internationalization

## Development

### Database Configuration

The application is configured to use PostgreSQL. Update your `.env` file if needed:

```env
DATABASE_URL="postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8"
```

### Running Tests

```bash
php bin/phpunit
```

### Debugging

The application includes Symfony's debug toolbar and profiler in development mode. Access the profiler at `/_profiler`.

### Code Quality

```bash
# Clear cache
php bin/console cache:clear

# Check routes
php bin/console debug:router

# Database schema validation
php bin/console doctrine:schema:validate
```

## Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Setup

1. Follow the installation instructions above
2. Make sure all tests pass: `php bin/phpunit`
3. Follow PSR-12 coding standards
4. Add tests for new features
5. Update documentation as needed

## Authors and Acknowledgments

- **Ronald Fagbehouro** - Developer
- **Syrder Baptichon** - Developer  
- **Amine Cheikh** - Developer

Created as a final project for Symfony framework learning.

## License

This project is proprietary software. All rights reserved.

## Project Status

This project is currently in active development as a learning exercise for Symfony framework and web development best practices.
