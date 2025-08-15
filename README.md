0# Bellevue Infrastructure Analysis Server

## Prerequisites

Make sure you have Node.js and npm installed on your system:
1. Download and install Node.js from [nodejs.org](https://nodejs.org/)
2. Verify installation by running:
```bash
node --version
npm --version
```

## API Authentication Setup

1. Create an account on [Bellevue's OpenData Portal](https://data.bellevuewa.gov/signup)
2. Go to your profile settings and navigate to "Developer Settings"
3. Create a new API token
4. Copy `.env.example` to `.env` and update with your credentials:
```bash
cp .env.example .env
```
5. Edit `.env` and fill in your:
   - BELLEVUE_APP_TOKEN (from Developer Settings)
   - BELLEVUE_USERNAME (your portal username)
   - BELLEVUE_PASSWORD (your portal password)

## Setup

1. Install dependencies:
```bash
npm install
```

2. Build the project:
```bash
npm run build
```

3. Start the server:
```bash
npm start
```

## Usage Example

With the server running, you can analyze recycling bin coverage using a POST request:
```bash
curl -X POST http://localhost:3001/analyze-recycling \
  -H "Content-Type: application/json" \
  -d '{"radius": 300, "min_ped_count": 8000}'
```

This will analyze areas with high pedestrian traffic (>8000 daily) that have fewer than 2 recycling bins within 300 meters.

## API Data Sources

The server uses the following Bellevue OpenData APIs:
1. Public Waste Receptacles Dataset
2. Pedestrian Count Program Dataset

If API credentials are not provided, the server will fall back to sample data covering major Bellevue neighborhoods.

## Environment Variables

- `BELLEVUE_APP_TOKEN`: Your Bellevue OpenData API token
- `BELLEVUE_USERNAME`: Your Bellevue OpenData username
- `BELLEVUE_PASSWORD`: Your Bellevue OpenData password
- `PORT`: Server port (default: 3001)

## Sample Data

The server includes sample data for Bellevue that is used when:
- API credentials are not configured
- API endpoints are unavailable
- API requests fail

Sample data covers major areas including:
- Downtown Bellevue
- Bellevue Square
- Crossroads
- Factoria
- Lake Hills
