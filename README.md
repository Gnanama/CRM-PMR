# CRM - Customer Management System

CRM Customer Inward/Outward & Work Allocation System with Vercel Web Analytics.

## Features

- Customer management (inward/outward tracking)
- Work allocation system
- Express.js backend server
- Vercel Web Analytics integration for monitoring and insights

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn package manager
- Vercel account (for deployment and analytics)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Gnanama/CRM-PMR.git
cd CRM-PMR
```

2. Install dependencies:
```bash
npm install
```

3. Set up environment variables:
```bash
cp .env.example .env
# Edit .env with your configuration
```

## Running the Application

### Development Mode
```bash
npm run dev
```
The server will start with hot-reload enabled on port 3000.

### Production Mode
```bash
npm start
```

Visit `http://localhost:3000` to access the application.

## Vercel Web Analytics

This project is configured with Vercel Web Analytics for tracking user interactions and page views.

### Setup

1. **Enable Analytics in Vercel Dashboard:**
   - Log in to [Vercel Dashboard](https://vercel.com/dashboard)
   - Select your project
   - Navigate to the "Analytics" tab
   - Click "Enable Web Analytics"

2. **Analytics Integration:**
   The analytics are already integrated in `public/index.html` using the `@vercel/analytics` package.

3. **Viewing Analytics Data:**
   - After deployment, visit your site
   - Return to the Vercel Analytics dashboard
   - Data will appear within a few minutes

For detailed setup instructions, see [vercel-analytics-setup.md](./vercel-analytics-setup.md)

## Deployment

### Deploy to Vercel

1. Install Vercel CLI:
```bash
npm i -g vercel
```

2. Deploy:
```bash
vercel deploy
```

3. Follow the prompts to complete deployment.

The `vercel.json` configuration is already set up for optimal deployment.

## Project Structure

```
.
├── server/
│   └── index.js          # Express server with API routes
├── public/
│   └── index.html        # Frontend HTML with Vercel Analytics
├── package.json          # Dependencies and scripts
├── vercel.json           # Vercel deployment configuration
├── vercel-analytics-setup.md  # Detailed analytics setup guide
└── README.md             # This file
```

## Environment Variables

Create a `.env` file based on `.env.example`:

- `PORT` - Server port (default: 3000)
- Add other required environment variables as needed

## Dependencies

### Main Dependencies
- `express` - Web framework
- `@vercel/analytics` - Vercel Web Analytics
- `bcryptjs` - Password hashing
- `better-sqlite3` - Database
- `jsonwebtoken` - JWT authentication
- `express-rate-limit` - API rate limiting
- `cookie-parser` - Cookie parsing
- `dotenv` - Environment variables
- `exceljs` - Excel file handling
- `pdfkit` - PDF generation

## API Endpoints

- `GET /` - Serves the main application page
- `GET /api/health` - Health check endpoint

Additional API endpoints will be added as the application develops.

## Security Features

- Rate limiting on all endpoints
- Cookie parsing for session management
- Environment variable configuration
- Error handling middleware

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is private and proprietary.

## Support

For issues and questions, please open an issue in the GitHub repository.

## Resources

- [Express Documentation](https://expressjs.com/)
- [Vercel Documentation](https://vercel.com/docs)
- [Vercel Analytics](https://vercel.com/analytics)
