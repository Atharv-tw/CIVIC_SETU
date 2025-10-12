# Contributing to CIVIC SETU

First off, thank you for considering contributing to CIVIC SETU! It's people like you that make this platform better for communities.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Pull Request Process](#pull-request-process)
- [Style Guidelines](#style-guidelines)
- [Community](#community)

## Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct:

- Be respectful and inclusive
- Welcome newcomers and encourage diverse perspectives
- Focus on what is best for the community
- Show empathy towards other community members

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check existing issues to avoid duplicates. When creating a bug report, include:

- **Clear title** and description
- **Steps to reproduce** the behavior
- **Expected behavior** vs actual behavior
- **Screenshots** or error logs (if applicable)
- **Environment details** (OS, browser, Node version, etc.)

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion, include:

- **Clear title** and detailed description
- **Use cases** - explain why this would be useful
- **Proposed solution** (if you have one)
- **Alternatives considered**

### Your First Code Contribution

Unsure where to begin? Look for issues labeled:
- `good first issue` - Good for newcomers
- `help wanted` - Extra attention needed
- `bug` - Something isn't working

### Pull Requests

1. Fork the repo and create your branch from `master`
2. If you've added code, add tests if applicable
3. Ensure the test suite passes
4. Make sure your code follows our style guidelines
5. Write a clear commit message
6. Open a pull request!

## Development Setup

### Prerequisites

- Node.js (v16+)
- MongoDB (local or Atlas)
- Git
- Expo CLI (for mobile development)

### Setup Steps

1. **Fork and Clone**
   ```bash
   git clone https://github.com/YOUR_USERNAME/CIVIC_SETU.git
   cd CIVIC_SETU
   ```

2. **Install Dependencies**
   ```bash
   # Backend
   cd civic-backend && npm install

   # Admin Dashboard
   cd ../civic-admin && npm install

   # Mobile App
   cd ../civic-mobile && npm install
   ```

3. **Environment Setup**
   ```bash
   # Copy .env.example to .env in each directory
   cp civic-backend/.env.example civic-backend/.env
   cp civic-admin/.env.example civic-admin/.env
   cp civic-mobile/.env.example civic-mobile/.env

   # Edit .env files with your local configuration
   ```

4. **Start Development Servers**
   ```bash
   # Terminal 1 - Backend
   cd civic-backend && npm run dev

   # Terminal 2 - Admin
   cd civic-admin && npm start

   # Terminal 3 - Mobile
   cd civic-mobile && npx expo start
   ```

## Pull Request Process

1. **Create a Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b bugfix/issue-you-are-fixing
   ```

2. **Make Your Changes**
   - Write clean, readable code
   - Follow existing patterns and conventions
   - Add comments for complex logic
   - Update documentation if needed

3. **Test Your Changes**
   ```bash
   # Run tests (if available)
   npm test

   # Test manually in browser/emulator
   # Ensure no console errors
   ```

4. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "feat: add amazing feature"
   # or
   git commit -m "fix: resolve issue with user login"
   ```

5. **Push and Create PR**
   ```bash
   git push origin feature/your-feature-name
   ```
   Then open a Pull Request on GitHub

6. **PR Description**
   Include:
   - What changes were made
   - Why these changes are necessary
   - How to test the changes
   - Screenshots (if UI changes)
   - Related issue numbers

## Style Guidelines

### Git Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add new feature
fix: bug fix
docs: documentation changes
style: formatting, missing semicolons, etc.
refactor: code refactoring
test: adding tests
chore: maintenance tasks
```

Examples:
```bash
feat: add push notification support
fix: resolve login redirect issue
docs: update API documentation
refactor: improve report filtering logic
```

### JavaScript/React Style

- Use **ES6+** features
- Use **functional components** with hooks
- Follow **Airbnb JavaScript Style Guide**
- Use **meaningful variable names**
- Keep functions **small and focused**

```javascript
// ✅ Good
const getUserReports = async (userId) => {
  const reports = await Report.find({ reporterId: userId });
  return reports;
};

// ❌ Avoid
function get(id) {
  return Report.find({reporterId:id})
}
```

### React Native / React

```jsx
// ✅ Good - Functional component with clear structure
const ReportCard = ({ report, onPress }) => {
  const [isExpanded, setIsExpanded] = useState(false);

  return (
    <TouchableOpacity onPress={onPress}>
      <Text>{report.title}</Text>
    </TouchableOpacity>
  );
};

// ❌ Avoid - Class components (unless necessary)
class ReportCard extends React.Component {
  // ...
}
```

### File Naming

- **Components**: `PascalCase` - `ReportCard.js`
- **Utilities**: `camelCase` - `formatDate.js`
- **Constants**: `UPPER_SNAKE_CASE` - `API_ENDPOINTS.js`
- **Styles**: Match component name - `ReportCard.styles.js`

### Code Organization

```
component/
├── ComponentName.js       # Main component
├── ComponentName.styles.js # Styles (if separate)
├── ComponentName.test.js  # Tests
└── index.js              # Export
```

### Comments

```javascript
// ✅ Good - Explain WHY, not WHAT
// Using setTimeout to debounce search input
// to avoid excessive API calls
const debouncedSearch = setTimeout(() => {
  searchReports(query);
}, 300);

// ❌ Avoid - Obvious comments
// Loop through reports
reports.forEach(report => {
  // ...
});
```

## Testing Guidelines

### Backend Testing

```javascript
describe('Report API', () => {
  it('should create a new report', async () => {
    const response = await request(app)
      .post('/api/reports')
      .send(mockReportData);

    expect(response.status).toBe(201);
    expect(response.body.title).toBe(mockReportData.title);
  });
});
```

### Frontend Testing

```javascript
import { render, fireEvent } from '@testing-library/react';

test('Report card displays title', () => {
  const { getByText } = render(<ReportCard report={mockReport} />);
  expect(getByText(mockReport.title)).toBeInTheDocument();
});
```

## Documentation

When adding new features:

- Update relevant documentation files
- Add JSDoc comments for functions
- Update README if needed
- Create/update API documentation

```javascript
/**
 * Fetches all reports for a specific user
 * @param {string} userId - The user's MongoDB ObjectId
 * @param {Object} filters - Optional filters (status, category)
 * @returns {Promise<Array>} Array of report objects
 */
async function getUserReports(userId, filters = {}) {
  // ...
}
```

## Community

### Questions?

- Open a GitHub Discussion
- Join our Discord (coming soon)
- Check existing documentation

### Stay Updated

- Star the repository
- Watch for releases
- Follow the project on social media

## Recognition

Contributors will be recognized in:
- README contributors section
- Release notes
- Project documentation

Thank you for contributing to CIVIC SETU! 🎉

---

**Note**: This is a living document. Suggestions for improvements are welcome!
