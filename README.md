# VoteNow - Real-time Polling Application

A complete, production-ready real-time polling web application built with Next.js, Firebase, and Tailwind CSS. Features ownership-based poll management, Google authentication, profile management with Cloudinary integration, and beautiful real-time visualizations.

## 🚀 Features

### Core Functionality
- **Real-time Polling**: Live vote updates using Firestore listeners
- **User Authentication**: Email/password + Google Sign-In with Firebase Auth
- **Ownership Model**: Users can only manage polls they created
- **Interactive Charts**: Beautiful visualizations using Chart.js
- **Responsive Design**: Mobile-first design with Tailwind CSS and Framer Motion
- **Secure Voting**: One vote per user with Firebase Security Rules

### Enhanced Features
- **Profile Management**: Update display name and profile picture
- **Google Integration**: Automatic profile picture from Google Sign-In
- **Cloudinary Upload**: Profile picture upload with image optimization
- **Vote History**: Track polls you've participated in
- **Social Sharing**: QR codes, social media sharing, and direct links
- **Real-time Analytics**: Live poll statistics and engagement metrics
- **Professional UI**: Modern animations and micro-interactions

## 🛠 Tech Stack

- **Frontend**: Next.js 15 (App Router), React, JavaScript
- **Styling**: Tailwind CSS, Framer Motion
- **Backend**: Firebase Firestore, Firebase Authentication
- **Charts**: Chart.js with react-chartjs-2
- **Image Upload**: Cloudinary
- **Icons**: Lucide React
- **Deployment**: Vercel-ready

## 📱 Pages & Features

### 1. Landing Page (/)
- Hero section with animated elements
- Join poll with poll ID
- Conditional authentication buttons
- Feature showcase with animations
- Professional footer with social links

### 2. Authentication (/auth)
- Enhanced form with proper icons
- Email & password authentication
- Google Sign-In integration
- Animated form transitions
- User registration with display name

### 3. Profile Management (/profile)
- Update display name and email
- Profile picture upload via Cloudinary
- Google profile picture integration
- Account statistics overview
- Professional form design

### 4. Create Poll (/create)
- Dynamic poll creation form
- Add/remove poll options (2-6 options)
- Poll preview functionality
- Category selection
- Automatic poll ID generation

### 5. Dashboard (/dashboard)
- View all user-created polls
- Search and filter functionality
- Poll management actions:
  - View poll
  - View results
  - End/reactivate poll
  - Reset votes
  - Delete poll
- Real-time poll statistics

### 6. Poll Voting (/poll/[pollId])
- Secure voting interface
- One vote per user enforcement
- Real-time vote count
- Automatic redirect to results
- Mobile-optimized design

### 7. Results (/results/[pollId])
- Live results with Chart.js
- Real-time updates via Firestore listeners
- Multiple chart types (bar, doughnut)
- Detailed vote breakdown
- Social sharing functionality
- QR code generation

### 8. Vote History (/history)
- Track polls you've voted in
- Delete vote history entries
- Filter and search functionality
- Engagement statistics

## 🗄 Database Schema

### Firestore Collections

```
polls/
├── {pollId}/
│   ├── question: string
│   ├── options: string[]
│   ├── createdBy: string (user UID)
│   ├── isActive: boolean
│   ├── createdAt: timestamp
│   ├── title?: string
│   └── category?: string
│
└── votes/
    └── {userId}/
        ├── optionIndex: number
        └── votedAt: timestamp

users/
└── {userId}/
    ├── email: string
    ├── displayName: string
    ├── photoURL: string
    ├── createdAt: timestamp
    └── updatedAt: timestamp

voteHistory/
└── {userId}/
    └── polls/
        └── {pollId}/
            ├── pollQuestion: string
            ├── selectedOption: string
            ├── votedAt: timestamp
            └── pollCreator: string
```

## 🔒 Security Rules

The application includes comprehensive Firestore Security Rules:

- **Authentication Required**: All operations require authentication
- **Poll Ownership**: Only poll creators can modify their polls
- **Vote Integrity**: Users can only vote once per poll
- **Profile Protection**: Users can only modify their own profile
- **Data Validation**: Strict data type and structure validation

## 🚀 Quick Start

### 1. Clone and Install
```bash
git clone <repository-url>
cd realtime-polling-app
npm install
```

### 2. Environment Setup
Create a `.env.local` file with your credentials:

```bash
# Firebase Configuration
NEXT_PUBLIC_FIREBASE_API_KEY=your_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id

# Cloudinary Configuration
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloud_name
NEXT_PUBLIC_CLOUDINARY_UPLOAD_PRESET=your_upload_preset
```

### 3. Firebase Setup
1. Create a new Firebase project at [Firebase Console](https://console.firebase.google.com)
2. Enable Authentication (Email/Password + Google)
3. Create Firestore database
4. Deploy the security rules from `firestore.rules`

### 4. Cloudinary Setup
1. Create a Cloudinary account
2. Create an unsigned upload preset named `VoteNow`
3. Configure the preset for profile pictures:
   - Folder: `profile_pictures`
   - Allowed formats: `jpg,png,gif,webp`
   - Max file size: `5MB`
   - Transformation: `c_fill,w_200,h_200,q_auto`

### 5. Run the Application
```bash
npm run dev
```

Visit `http://localhost:3000` to see the application.

## 📦 Project Structure

```
├── app/
│   ├── auth/page.js              # Enhanced authentication
│   ├── create/page.js            # Poll creation with preview
│   ├── dashboard/page.js         # User dashboard with search
│   ├── profile/page.js           # Profile management
│   ├── history/page.js           # Vote history
│   ├── poll/[pollId]/page.js     # Voting interface
│   ├── results/[pollId]/page.js  # Results with sharing
│   ├── contexts/AuthContext.js   # Authentication context
│   ├── globals.css               # Global styles with animations
│   ├── layout.js                 # Root layout
│   └── page.js                   # Enhanced landing page
├── components/
│   ├── Navbar.js                 # Navigation with animations
│   ├── PollChart.js              # Chart component
│   ├── ProtectedRoute.js         # Route protection
│   ├── QRCodeGenerator.js        # QR code generation
│   └── ShareModal.js             # Social sharing modal
├── lib/
│   ├── firebase.js               # Firebase configuration
│   └── cloudinary.js             # Cloudinary integration
├── firestore.rules               # Security rules
├── SETUP.md                      # Setup instructions
├── TROUBLESHOOTING.md            # Common issues and solutions
└── package.json                  # Dependencies
```

## 🎨 UI/UX Enhancements

### Design System
- **Color Palette**: Primary blues and purples with gradients
- **Typography**: Modern font hierarchy with proper spacing
- **Animations**: Framer Motion for smooth interactions
- **Icons**: Lucide React for consistent iconography
- **Responsive**: Mobile-first approach with breakpoints

### Interactive Elements
- **Hover Effects**: Subtle scale and color transitions
- **Loading States**: Animated spinners and skeletons
- **Form Validation**: Real-time feedback with icons
- **Micro-interactions**: Button presses, form focus states
- **Page Transitions**: Smooth navigation animations

### Accessibility
- **WCAG Compliant**: Proper contrast ratios and focus states
- **Keyboard Navigation**: Full keyboard accessibility
- **Screen Reader**: Semantic HTML and ARIA labels
- **Color Blind Friendly**: Accessible color combinations

## 🔧 Configuration Files

- `tailwind.config.js` - Extended Tailwind configuration with custom colors
- `next.config.js` - Next.js configuration
- `postcss.config.js` - PostCSS configuration
- `firestore.rules` - Firebase Security Rules
- `.env.example` - Environment variables template

## 🚀 Deployment

### Vercel Deployment (Recommended)
1. Push code to GitHub
2. Connect repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy automatically

### Environment Variables for Production
```bash
NEXT_PUBLIC_FIREBASE_API_KEY=production_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=production_domain
NEXT_PUBLIC_FIREBASE_PROJECT_ID=production_project
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=production_bucket
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=production_sender
NEXT_PUBLIC_FIREBASE_APP_ID=production_app_id
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=production_cloud
NEXT_PUBLIC_CLOUDINARY_UPLOAD_PRESET=production_preset
```

## 🔐 Security Features

- **Authentication Required**: All features require user authentication
- **Ownership Validation**: Users can only manage their own content
- **Vote Integrity**: Firestore rules prevent duplicate voting
- **Data Validation**: Client and server-side validation
- **Secure Rules**: Comprehensive Firestore Security Rules
- **Image Upload**: Secure Cloudinary integration with file validation

## 📊 Real-time Features

- **Live Vote Updates**: Results update instantly without refresh
- **Real-time Counters**: Vote counts update in real-time
- **Automatic Sync**: All clients see updates simultaneously
- **Offline Support**: Firebase handles offline scenarios
- **Connection Status**: Visual indicators for connection state

## 🎯 Performance Optimizations

- **Code Splitting**: Automatic route-based code splitting
- **Image Optimization**: Cloudinary transformations and Next.js Image
- **Lazy Loading**: Components and images load on demand
- **Caching**: Firebase caching and browser caching strategies
- **Bundle Analysis**: Optimized bundle sizes

## 📱 Mobile Experience

- **Touch Optimized**: Large touch targets and gestures
- **Responsive Charts**: Charts adapt to screen size
- **Mobile Navigation**: Collapsible navigation menu
- **Swipe Gestures**: Natural mobile interactions
- **PWA Ready**: Service worker and manifest configuration

## 🧪 Testing & Quality

- **Error Boundaries**: Graceful error handling
- **Loading States**: Comprehensive loading indicators
- **Form Validation**: Real-time validation with feedback
- **Edge Cases**: Handling of empty states and errors
- **Cross-browser**: Tested on major browsers

## 📈 Analytics & Monitoring

- **Vote Tracking**: Detailed voting analytics
- **User Engagement**: Poll participation metrics
- **Performance Monitoring**: Real-time performance insights
- **Error Tracking**: Comprehensive error logging

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support & Troubleshooting

For common issues, check [TROUBLESHOOTING.md](TROUBLESHOOTING.md).

For setup instructions, see [SETUP.md](SETUP.md).

### Common Issues:
- **Cloudinary Upload Errors**: Ensure upload preset is "unsigned"
- **Firebase Connection**: Check environment variables and security rules
- **Authentication Issues**: Verify Firebase Auth configuration
- **Real-time Updates**: Ensure Firestore listeners are properly configured

---

**Built with ❤️ for engaging real-time experiences**

*VoteNow - Where every vote counts and every voice matters.*