name: FrontendCI

on: [push, pull_request]

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [12.x, 14.x]

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Set up Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v1
      with:
        node-version: ${{ matrix.node-version }}
    
    - name: Install dependencies
      working-directory: ./frontend
      run: npm install
    
    - name: Format
      working-directory: ./frontend/src
      run: |
          npm run format:check
    
    - name: Run ESLint
      working-directory: ./frontend/src
      run: |
          npm run lint
      
    - name: Run the tests and generate coverage report
      working-directory: ./frontend
      run: npm test -- --coverage
        
    - name: Upload coverage to Codecov
      uses: codecov/codecov-action@v1

    - name: Build
      working-directory: ./frontend
      run: npm run build --if-present
