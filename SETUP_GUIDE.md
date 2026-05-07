# Linehaul Truck Request System - Setup Guide

## Prerequisites

1. **Appwrite Server** - You need an Appwrite instance running. Follow [Appwrite installation guide](https://appwrite.io/docs/quick-start)
2. **Node.js** 18+ 
3. **npm** or **yarn**

## Environment Setup

### 1. Create `.env.local` file

Create a `.env.local` file in `/starter-for-nextjs/` directory with the following variables:

```env
# Appwrite Configuration
NEXT_PUBLIC_APPWRITE_ENDPOINT=http://localhost:80/v1
NEXT_PUBLIC_APPWRITE_PROJECT_ID=your_project_id
NEXT_PUBLIC_APPWRITE_DATABASE_ID=linehaul_db
NEXT_PUBLIC_APPWRITE_PROJECT_NAME=Linehaul Request System
```

### 2. Configure Appwrite

#### Create Database
1. Go to your Appwrite Console
2. Create a new database named `linehaul_db`
3. Copy the database ID and update `NEXT_PUBLIC_APPWRITE_DATABASE_ID` in `.env.local`

#### Create Collection
1. In the `linehaul_db` database, create a collection named `requests`
2. Add the following attributes:

| Attribute | Type | Required | Default |
|-----------|------|----------|---------|
| userId | String | Yes | - |
| cluster | String | Yes | - |
| dock | String | Yes | - |
| region | String | Yes | - |
| backlogs | Number | Yes | - |
| backlogsTimestamp | String | Yes | - |
| status | String | Yes | "pending" |
| createdAt | String | No | - |
| updatedAt | String | No | - |

#### Enable Authentication
1. Go to Settings > Providers in Appwrite Console
2. Enable Email/Password authentication
3. Configure permissions for the `requests` collection to allow authenticated users to read/write

## Installation

```bash
cd starter-for-nextjs

# Install dependencies
npm install

# Start development server
npm run dev
```

The app will be available at `http://localhost:3000`

## Features

✅ **User Authentication** - Email/Password login and signup  
✅ **Create Requests** - Submit new truck requests with:
  - Cluster
  - Dock #
  - Region
  - Backlogs count
  - Backlogs timestamp

✅ **View Requests** - Dashboard displaying all requests with filtering  
✅ **Approve/Reject** - Manage request status (pending → approved/rejected)  
✅ **Delete Requests** - Remove requests from the system  
✅ **Status Tracking** - Track request lifecycle

## Usage

1. **Sign Up / Sign In**
   - Create a new account or sign in with existing credentials
   
2. **Create a New Request**
   - Click "+ New Request" button
   - Fill in all required fields
   - Click "Save Request"

3. **View All Requests**
   - Dashboard shows all requests in a table format
   - Filter by status: All, Pending, Approved, Rejected

4. **Approve/Reject Requests**
   - Click "Approve" or "Reject" buttons on pending requests
   - Status will update immediately

5. **Delete Requests**
   - Click "Delete" button to remove a request

## Production Build

```bash
npm run build
npm start
```

## Troubleshooting

### "Failed to authenticate" error
- Check that your Appwrite instance is running
- Verify Appwrite endpoint in environment variables
- Ensure CORS is properly configured in Appwrite

### "Failed to save request"
- Verify database ID and collection name match your Appwrite setup
- Check collection attributes match the schema above
- Ensure proper permissions are set in Appwrite

### Can't access app
- Verify all environment variables are set
- Check that `npm install` completed successfully
- Clear browser cache and local storage

## Next Steps

- Add email notifications
- Implement request editing
- Add export to CSV/Excel
- Implement user roles (Admin, Approver, Requester)
- Add request search and advanced filtering
