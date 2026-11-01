# Richfield Connect


## 1. Introduction

For my Web Technology 512 assignment, I developed a website called **Richfield Connect**. The idea behind the project is to give students a place where they can create an academic profile, share information and interact with other students. It is meant to be a simple and professional platform focused on learning and communication.

I built the website using React and JavaScript. It is a single-page application, which means users can move between the different pages without the whole website reloading each time. The project runs in a browser and does not need a database or backend server. The information entered by a user is saved in the browser using `localStorage`.

I used Richfield Blue (`#003087`), white and grey for the design to keep the website neat and consistent with the colours required in the assignment.

## 2. Technologies used

The following tools and technologies were used to develop the project:

| Technology | How I used it |
| --- | --- |
| React 18 | To build the website using reusable components |
| JavaScript and JSX | To write the application logic and display content |
| Vite 5 | To create the React project and run it during development |
| React Router v6 | To move between pages without refreshing the website |
| `useState` | To manage form inputs and other values that change |
| Context API and `useReducer` | To manage the registered student and the posts in one place |
| `useEffect` | To help load and save information in browser storage |
| `localStorage` | To keep student details and posts after a page refresh |
| CSS | To style the pages and make them work on different screen sizes |

## 3. Main pages of the website

The application has the five pages required in the assignment:

| Page | Route | What the page does |
| --- | --- | --- |
| Home | `/` | Introduces Richfield Connect and provides a link to registration |
| About | `/about` | Explains the purpose of the platform and its community guidelines |
| Sign Up | `/signup` | Allows a student to complete a registration form and see a live preview |
| Profile | `/profile` | Displays the information saved when the student registers |
| Feed | `/feed` | Allows students to create posts, like or unlike posts and delete posts |

I also included a page that appears when someone tries to open a route that does not exist. The navigation bar and footer are shown throughout the website.

## 4. How the main features work

### 4.1 Student registration

The registration page asks for a student's full name, student number, campus, email address, password, interests and a short biography. The student must also confirm the password and accept the terms and conditions.

I used controlled form inputs with `useState`. The form checks for mistakes, such as an empty name, an invalid email address or a student number that is too short. It shows error messages below the relevant fields. The checks run when the student leaves a field and again when the form is submitted.

Next to the form is a profile preview. As the student types, the preview shows their name, campus, biography and selected interests. After successful registration, the student is taken to the Profile page.

### 4.2 Student profile

The Profile page displays the information that the student entered during registration. It includes an avatar made from the student's initials, as well as their campus, student number, email, interests and biography. If nobody has registered in the browser, the page asks the visitor to sign up first.

The page also has a small statistics section for posts, connections and groups. Connections and groups are display-only values because the assignment does not require those features to be developed.

### 4.3 Posts and interactions

On the Feed page, the student can write and publish a post. Each post includes the student's name, the date and time, and the message that was posted. New posts appear at the top of the feed without reloading the page.

Students can like a post and remove the like by clicking the button again. They can also delete their own posts. The website asks for confirmation before deleting a post.

I added editing and commenting as extra features because the assignment scenario also mentions managing content and interacting with other students.

### 4.4 Saving data

I used React's Context API together with `useReducer` so that the Profile and Feed pages can use the same information. The main actions are `REGISTER_USER`, `ADD_POST`, `TOGGLE_LIKE` and `DELETE_POST`. The project also uses actions for editing posts, adding comments and restoring saved data.

Student information and posts are saved in `localStorage`. This means they can still appear after refreshing the browser. The information is only saved in the browser being used; it is not shared with other devices.

## 5. Project folder structure

```text
Richfield_Connect_Project/
├── README.md
├── index.html
├── package.json
├── vite.config.js
├── public/
│   └── favicon.svg
├── src/
│   ├── main.jsx
│   ├── App.jsx
│   ├── App.css
│   ├── components/
│   │   ├── CreatePost.jsx
│   │   ├── EmptyState.jsx
│   │   ├── Footer.jsx
│   │   ├── Navbar.jsx
│   │   ├── PageHeading.jsx
│   │   ├── Post.jsx
│   │   ├── ProfilePreview.jsx
│   │   └── SignUpForm.jsx
│   ├── context/
│   │   └── AppContext.jsx
│   ├── pages/
│   │   ├── About.jsx
│   │   ├── Feed.jsx
│   │   ├── Home.jsx
│   │   ├── NotFound.jsx
│   │   ├── Profile.jsx
│   │   └── SignUp.jsx
│   └── utils/
│       ├── constants.js
│       ├── formatters.js
│       ├── storage.js
│       └── validation.js
└── documentation/
    ├── ASSIGNMENT_COVER_PAGE.pdf
    ├── PROJECT_REPORT.pdf
    ├── RUBRIC_CHECKLIST.md
    └── TESTING_GUIDE.md
```

The `components` folder contains parts of the interface that can be reused. The `pages` folder contains the different views of the website. I placed the shared state in `context` and helper functions in `utils` to make the project easier to organise and understand.

## 6. How to run the project

To run Richfield Connect, you need **Node.js**, **npm**, a code editor such as Visual Studio Code, and a web browser.

1. Extract the ZIP folder containing the project.
2. Open the `Richfield_Connect_Project` folder in Visual Studio Code.
3. Open a new terminal and make sure you are in the folder containing `package.json`.
4. Install the required packages.
5. Start the Vite development server.
6. Open the local link shown in the terminal, usually `http://localhost:5173/`.

**Windows PowerShell commands:**

```powershell
node -v
npm.cmd -v
npm.cmd install
npm.cmd run dev
```

I used `npm.cmd` in these instructions because some Windows PowerShell setups block `npm.ps1`. Using `npm.cmd` avoids that problem without changing the computer's PowerShell settings.

**Command Prompt, macOS or Linux:**

```bash
npm install
npm run dev
```

To create a production build, run `npm.cmd run build` on Windows PowerShell (or `npm run build` on other terminals). The build output is placed in the `dist` folder.

## 7. Design and testing

The website uses the blue, white and grey colour scheme required by Richfield. I used CSS for the layout, buttons, form fields and cards. I also included hover and focus effects, as well as responsive styling for phones, tablets and desktop screens.

The following are the main things to check when testing the project:

- All five pages open correctly using the navigation links.
- The Sign Up form shows useful messages for missing or incorrect information.
- The profile preview changes while the student completes the form.
- The Profile page displays the information saved during registration.
- Posts can be created, liked, unliked and deleted.
- Saved information is still available after refreshing the browser.
- The layout remains readable on smaller screens.

The detailed testing steps are also included in `documentation/TESTING_GUIDE.md`.

## 8. Project limitations

Richfield Connect is a **front-end demonstration project**, not a real online student account system. It does not have a database, secure login system or connection between different users' devices. The most recently registered person in a browser is treated as the active user in that browser.

The registration form checks the password and confirmation, but it does not save the actual password in `localStorage`, because that would not be secure. Users should not enter a password that they use for a real account. The contact details on the About page are examples for this project and should not be treated as official Richfield contact details.

## 9. Conclusion

This project helped me put the React concepts from Web Technology 512 into practice. I worked with components, props, forms, state management, routing and browser storage while building a website with different pages and interactive features. It also gave me practice in organising code and making a website that can be used on different screen sizes.

## 10. References

Richfield Graduate Institute of Technology (2026) *Web Technology 512 Student Guide*. Second-semester module guide. Richfield Graduate Institute of Technology.

Richfield Graduate Institute of Technology (2026) *Web Technology 512 Assignment: Richfield Connect*. Assignment brief and assessment rubric. Richfield Graduate Institute of Technology.

React (n.d.) *React documentation*. Available at: https://react.dev/ (Accessed: 25 October 2026).

React Router (n.d.) *React Router documentation*. Available at: https://reactrouter.com/ (Accessed: 25 October 2026).

Vite (n.d.) *Vite documentation*. Available at: https://vite.dev/ (Accessed: 25 October 2026).

MDN Web Docs (n.d.) *Window: localStorage property*. Available at: https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage (Accessed: 25 October 2026).
# Richfield Connect


## 1. Introduction

For my Web Technology 512 assignment, I developed a website called **Richfield Connect**. The idea behind the project is to give students a place where they can create an academic profile, share information and interact with other students. It is meant to be a simple and professional platform focused on learning and communication.

I built the website using React and JavaScript. It is a single-page application, which means users can move between the different pages without the whole website reloading each time. The project runs in a browser and does not need a database or backend server. The information entered by a user is saved in the browser using `localStorage`.

I used Richfield Blue (`#003087`), white and grey for the design to keep the website neat and consistent with the colours required in the assignment.

## 2. Technologies used

The following tools and technologies were used to develop the project:

| Technology | How I used it |
| --- | --- |
| React 18 | To build the website using reusable components |
| JavaScript and JSX | To write the application logic and display content |
| Vite 5 | To create the React project and run it during development |
| React Router v6 | To move between pages without refreshing the website |
| `useState` | To manage form inputs and other values that change |
| Context API and `useReducer` | To manage the registered student and the posts in one place |
| `useEffect` | To help load and save information in browser storage |
| `localStorage` | To keep student details and posts after a page refresh |
| CSS | To style the pages and make them work on different screen sizes |

## 3. Main pages of the website

The application has the five pages required in the assignment:

| Page | Route | What the page does |
| --- | --- | --- |
| Home | `/` | Introduces Richfield Connect and provides a link to registration |
| About | `/about` | Explains the purpose of the platform and its community guidelines |
| Sign Up | `/signup` | Allows a student to complete a registration form and see a live preview |
| Profile | `/profile` | Displays the information saved when the student registers |
| Feed | `/feed` | Allows students to create posts, like or unlike posts and delete posts |

I also included a page that appears when someone tries to open a route that does not exist. The navigation bar and footer are shown throughout the website.

## 4. How the main features work

### 4.1 Student registration

The registration page asks for a student's full name, student number, campus, email address, password, interests and a short biography. The student must also confirm the password and accept the terms and conditions.

I used controlled form inputs with `useState`. The form checks for mistakes, such as an empty name, an invalid email address or a student number that is too short. It shows error messages below the relevant fields. The checks run when the student leaves a field and again when the form is submitted.

Next to the form is a profile preview. As the student types, the preview shows their name, campus, biography and selected interests. After successful registration, the student is taken to the Profile page.

### 4.2 Student profile

The Profile page displays the information that the student entered during registration. It includes an avatar made from the student's initials, as well as their campus, student number, email, interests and biography. If nobody has registered in the browser, the page asks the visitor to sign up first.

The page also has a small statistics section for posts, connections and groups. Connections and groups are display-only values because the assignment does not require those features to be developed.

### 4.3 Posts and interactions

On the Feed page, the student can write and publish a post. Each post includes the student's name, the date and time, and the message that was posted. New posts appear at the top of the feed without reloading the page.

Students can like a post and remove the like by clicking the button again. They can also delete their own posts. The website asks for confirmation before deleting a post.

I added editing and commenting as extra features because the assignment scenario also mentions managing content and interacting with other students.

### 4.4 Saving data

I used React's Context API together with `useReducer` so that the Profile and Feed pages can use the same information. The main actions are `REGISTER_USER`, `ADD_POST`, `TOGGLE_LIKE` and `DELETE_POST`. The project also uses actions for editing posts, adding comments and restoring saved data.

Student information and posts are saved in `localStorage`. This means they can still appear after refreshing the browser. The information is only saved in the browser being used; it is not shared with other devices.

## 5. Project folder structure

```text
Richfield_Connect_Project/
├── README.md
├── index.html
├── package.json
├── vite.config.js
├── public/
│   └── favicon.svg
├── src/
│   ├── main.jsx
│   ├── App.jsx
│   ├── App.css
│   ├── components/
│   │   ├── CreatePost.jsx
│   │   ├── EmptyState.jsx
│   │   ├── Footer.jsx
│   │   ├── Navbar.jsx
│   │   ├── PageHeading.jsx
│   │   ├── Post.jsx
│   │   ├── ProfilePreview.jsx
│   │   └── SignUpForm.jsx
│   ├── context/
│   │   └── AppContext.jsx
│   ├── pages/
│   │   ├── About.jsx
│   │   ├── Feed.jsx
│   │   ├── Home.jsx
│   │   ├── NotFound.jsx
│   │   ├── Profile.jsx
│   │   └── SignUp.jsx
│   └── utils/
│       ├── constants.js
│       ├── formatters.js
│       ├── storage.js
│       └── validation.js
└── documentation/
    ├── ASSIGNMENT_COVER_PAGE.pdf
    ├── PROJECT_REPORT.pdf
    ├── RUBRIC_CHECKLIST.md
    └── TESTING_GUIDE.md
```

The `components` folder contains parts of the interface that can be reused. The `pages` folder contains the different views of the website. I placed the shared state in `context` and helper functions in `utils` to make the project easier to organise and understand.

## 6. How to run the project

To run Richfield Connect, you need **Node.js**, **npm**, a code editor such as Visual Studio Code, and a web browser.

1. Extract the ZIP folder containing the project.
2. Open the `Richfield_Connect_Project` folder in Visual Studio Code.
3. Open a new terminal and make sure you are in the folder containing `package.json`.
4. Install the required packages.
5. Start the Vite development server.
6. Open the local link shown in the terminal, usually `http://localhost:5173/`.

**Windows PowerShell commands:**

```powershell
node -v
npm.cmd -v
npm.cmd install
npm.cmd run dev
```

I used `npm.cmd` in these instructions because some Windows PowerShell setups block `npm.ps1`. Using `npm.cmd` avoids that problem without changing the computer's PowerShell settings.

**Command Prompt, macOS or Linux:**

```bash
npm install
npm run dev
```

To create a production build, run `npm.cmd run build` on Windows PowerShell (or `npm run build` on other terminals). The build output is placed in the `dist` folder.

## 7. Design and testing

The website uses the blue, white and grey colour scheme required by Richfield. I used CSS for the layout, buttons, form fields and cards. I also included hover and focus effects, as well as responsive styling for phones, tablets and desktop screens.

The following are the main things to check when testing the project:

- All five pages open correctly using the navigation links.
- The Sign Up form shows useful messages for missing or incorrect information.
- The profile preview changes while the student completes the form.
- The Profile page displays the information saved during registration.
- Posts can be created, liked, unliked and deleted.
- Saved information is still available after refreshing the browser.
- The layout remains readable on smaller screens.

The detailed testing steps are also included in `documentation/TESTING_GUIDE.md`.

## 8. Project limitations

Richfield Connect is a **front-end demonstration project**, not a real online student account system. It does not have a database, secure login system or connection between different users' devices. The most recently registered person in a browser is treated as the active user in that browser.

The registration form checks the password and confirmation, but it does not save the actual password in `localStorage`, because that would not be secure. Users should not enter a password that they use for a real account. The contact details on the About page are examples for this project and should not be treated as official Richfield contact details.

## 9. Conclusion

This project helped me put the React concepts from Web Technology 512 into practice. I worked with components, props, forms, state management, routing and browser storage while building a website with different pages and interactive features. It also gave me practice in organising code and making a website that can be used on different screen sizes.

## 10. References

Richfield Graduate Institute of Technology (2026) *Web Technology 512 Student Guide*. Second-semester module guide. Richfield Graduate Institute of Technology.

Richfield Graduate Institute of Technology (2026) *Web Technology 512 Assignment: Richfield Connect*. Assignment brief and assessment rubric. Richfield Graduate Institute of Technology.

React (n.d.) *React documentation*. Available at: https://react.dev/ (Accessed: 25 October 2026).

React Router (n.d.) *React Router documentation*. Available at: https://reactrouter.com/ (Accessed: 25 October 2026).

Vite (n.d.) *Vite documentation*. Available at: https://vite.dev/ (Accessed: 25 October 2026).

MDN Web Docs (n.d.) *Window: localStorage property*. Available at: https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage (Accessed: 25 October 2026).
