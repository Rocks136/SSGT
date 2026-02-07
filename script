// Simple user storage (in production, use a backend)
let users = JSON.parse(localStorage.getItem('users')) || {};
let feedbacks = JSON.parse(localStorage.getItem('feedbacks')) || [];

// Login Form
document.getElementById('loginForm')?.addEventListener('submit', function(e) {
    e.preventDefault();
    const username = document.getElementById('username').value;
    const password = document.getElementById('password').value;
    const message = document.getElementById('message');

    if (username === 'Bhanuchand' && password === 'Prataap') {
        localStorage.setItem('currentUser', 'owner');
        window.location.href = 'welcome.html';
    } else if (users[username] && users[username] === password) {
        localStorage.setItem('currentUser', username);
        window.location.href = 'welcome.html';
    } else {
        message.textContent = 'Invalid credentials!';
    }
});

// Sign Up
document.getElementById('signupBtn')?.addEventListener('click', function() {
    const username = prompt('Enter your name (username):');
    const password = prompt('Enter a password:');
    if (username && password) {
        users[username] = password;
        localStorage.setItem('users', JSON.stringify(users));
        alert('Sign up successful! Please login.');
    }
});

// Forgot Password
document.getElementById('forgotBtn')?.addEventListener('click', function() {
    const username = prompt('Enter your username:');
    if (users[username]) {
        alert('Password reset link sent to your email (demo: check console). In real app, integrate email.');
        console.log(`Reset link for ${username}`);
    } else {
        alert('Username not found.');
    }
});

// Welcome Page
if (window.location.pathname.includes('welcome.html')) {
    const user = localStorage.getItem('currentUser');
    document.getElementById('userName').textContent = user === 'owner' ? 'Owner' : user;
}

// Feedback Form
document.getElementById('feedbackForm')?.addEventListener('submit', function(e) {
    e.preventDefault();
    const feedbackText = document.getElementById('feedbackText').value;
    const user = localStorage.getItem('currentUser');
    feedbacks.push({ user, text: feedbackText, date: new Date().toLocaleString() });
    localStorage.setItem('feedbacks', JSON.stringify(feedbacks));
    alert('Feedback submitted!');
    document.getElementById('feedbackText').value = '';
});

// Show Feedback for Owner
if (window.location.pathname.includes('feedback.html') && localStorage.getItem('currentUser') === 'owner') {
    document.getElementById('feedbackList').style.display = 'block';
    const list = document.getElementById('feedbackItems');
    feedbacks.forEach(f => {
        const li = document.createElement('li');
        li.textContent = `${f.user} (${f.date}): ${f.text}`;
        list.appendChild(li);
    });
}

// Logout
function logout() {
    localStorage.removeItem('currentUser');
    window.location.href = 'index.html';
}