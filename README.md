<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ArtShare - Share Your Artworks</title>
    <link rel="stylesheet" href="style.css">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <!-- Firebase SDKs -->
    <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-auth-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-storage-compat.js"></script>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <div class="nav-container">
            <div class="nav-logo">
                <i class="fas fa-palette"></i>
                <span>ArtShare</span>
            </div>
            <div class="nav-menu" id="nav-menu">
                <a href="#" class="nav-link active" onclick="showSection('feed')">Feed</a>
                <a href="#" class="nav-link" onclick="showSection('upload')">Upload</a>
                <a href="#" class="nav-link" onclick="showSection('profile')">Profile</a>
                <button class="login-btn" id="loginBtn">
                    <i class="fas fa-sign-in-alt"></i> Login
                </button>
            </div>
        </div>
    </nav>

    <!-- Auth Modal -->
    <div id="authModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeAuthModal()">&times;</span>
            <div id="loginForm">
                <h2>Login to ArtShare</h2>
                <p>Owner: <strong>samsungbbg54@gmail.com</strong></p>
                <form id="login-form">
                    <input type="email" id="email" placeholder="Email" required>
                    <input type="password" id="password" placeholder="Password" required>
                    <button type="submit">Login</button>
                </form>
                <p>Don't have an account? <a href="#" onclick="showSignup()">Sign up</a></p>
            </div>
            <div id="signupForm" style="display: none;">
                <h2>Create Account</h2>
                <form id="signup-form">
                    <input type="text" id="displayName" placeholder="Display Name" required>
                    <input type="email" id="signupEmail" placeholder="Email" required>
                    <input type="password" id="signupPassword" placeholder="Password" required>
                    <button type="submit">Sign Up</button>
                </form>
                <p>Have an account? <a href="#" onclick="showLogin()">Login</a></p>
            </div>
        </div>
    </div>

    <!-- Main Content -->
    <main class="main-container">
        <!-- Feed Section -->
        <section id="feed" class="section active">
            <div class="section-header">
                <h1>Art Feed</h1>
                <p>Discover amazing artworks from the community</p>
            </div>
            <div class="artwork-grid" id="artworkGrid">
                <div class="loading">Loading artworks...</div>
            </div>
        </section>

        <!-- Upload Section -->
        <section id="upload" class="section">
            <div class="section-header">
                <h1>Upload Your Artwork</h1>
                <p>Share your creativity with the world</p>
            </div>
            <form id="uploadForm" class="upload-form">
                <div class="upload-area" id="uploadArea">
                    <i class="fas fa-cloud-upload-alt"></i>
                    <p>Drag & drop your artwork or click to browse</p>
                    <input type="file" id="artworkFile" accept="image/*" required>
                </div>
                <input type="text" id="artworkTitle" placeholder="Artwork Title" required>
                <textarea id="artworkDescription" placeholder="Description (optional)"></textarea>
                <button type="submit">Share Artwork</button>
            </form>
        </section>

        <!-- Profile Section -->
        <section id="profile" class="section">
            <div class="section-header">
                <h1>Your Profile</h1>
            </div>
            <div id="profileContent" class="profile-content">
                <div class="loading">Please login to view profile</div>
            </div>
        </section>
    </main>

    <!-- Artwork Modal -->
    <div id="artworkModal" class="modal">
        <div class="modal-content large">
            <span class="close" onclick="closeArtworkModal()">&times;</span>
            <div class="artwork-modal-body" id="artworkModalBody">
                <!-- Artwork details will be loaded here -->
            </div>
        </div>
    </div>

    <script src="firebase-config.js"></script>
    <script src="script.js"></script>
</body>
</html>
