# Make-up-products-
knowing the different product of make up 
<think>
The user wants a website about makeup products.
The key requirements are:
1.  **Topic:** Makeup products.
2.  **Specific Content:** A "Cookies" section, a "Policy" section, and a "Privacy" section.
3.  **Length:** "Make it long" - this implies substantial content, multiple sections, and a detailed layout, not just a single paragraph.
4.  **Design:** "Make a design" - this requires CSS styling to make it look professional and aesthetic (likely soft colors, elegant fonts, grid layouts for products).

**Plan:**
1.  **Structure (HTML):**
    *   **Header:** Logo, Navigation (Home, Shop, About, Contact, Legal).
    *   **Hero Section:** Big banner image, catchy headline, CTA button.
    *   **Featured Products:** A grid of makeup items with prices and "Add to Cart" buttons.
    *   **About Section:** Brand story.
    *   **Blog/News Section:** Tips on makeup application.
    *   **Footer:** Links to the requested legal pages.
    *   **Modals/Hidden Sections:** Since I can't build a multi-page site in a single code block easily, I will create a "Legal" section at the bottom that expands or is clearly visible, containing the Privacy Policy and Cookie Policy.

2.  **Style (CSS):**
    *   **Color Palette:** Soft pinks, rose gold, white, and dark grey for text. This is standard for beauty brands.
    *   **Typography:** A serif font for headings (elegant) and sans-serif for body text (readable).
    *   **Layout:** Flexbox and Grid for responsiveness.
    *   **Visuals:** I will use placeholder images (via unsplash source) to make it look real.

3.  **Content (The "Long" part):**
    *   I need to write actual text for the Privacy Policy and Cookie Policy. These are usually long legal documents. I will draft realistic-sounding legal text for a fictional brand called "Lumina Beauty."

4.  **Refinement:**
    *   Ensure the "Cookie Policy" is distinct.
    *   Make sure the design looks modern (shadows, rounded corners, hover effects).

**Drafting the Code:**
*   *HTML:* Standard semantic tags (`header`, `main`, `section`, `footer`).
*   *CSS:* Embedded in `<style>` tags for a single-file solution.
*   *JS:* Simple script to handle the "Accept Cookies" banner interaction.

Let's assemble the code.
</think>Here is a complete, single-file solution containing the HTML, CSS, and JavaScript. I have designed a modern, elegant beauty brand called **"Lumina Beauty"** with a focus on a soft, rose-gold aesthetic.

This code includes a full homepage, a product showcase, and detailed **Privacy Policy** and **Cookie Policy** sections as requested.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lumina Beauty | Premium Cosmetics</title>
    <style>
        /* --- CSS VARIABLES & RESET --- */
        :root {
            --primary-color: #d4a373; /* Gold/Bronze */
            --secondary-color: #faedcd; /* Cream */
            --accent-color: #e5989b; /* Soft Pink */
            --text-dark: #333333;
            --text-light: #666666;
            --white: #ffffff;
            --font-heading: 'Playfair Display', serif;
            --font-body: 'Lato', sans-serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-body);
            color: var(--text-dark);
            line-height: 1.6;
            background-color: #fdfdfd;
        }

        /* --- TYPOGRAPHY --- */
        h1, h2, h3, h4 {
            font-family: var(--font-heading);
            font-weight: 700;
        }

        a {
            text-decoration: none;
            color: inherit;
            transition: 0.3s;
        }

        /* --- HEADER & NAV --- */
        header {
            background-color: var(--white);
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .navbar {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-family: var(--font-heading);
            color: var(--primary-color);
            letter-spacing: 1px;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
        }

        .nav-links a:hover {
            color: var(--accent-color);
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: var(--white);
            padding: 0.8rem 1.5rem;
            border-radius: 30px;
            font-weight: bold;
        }

        .btn-primary:hover {
            background-color: #b08d55;
        }

        /* --- HERO SECTION --- */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.1), rgba(0,0,0,0.1)), url('https://images.unsplash.com/photo-1596462502278-27bfdd403348?ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80');
            background-size: cover;
            background-position: center;
            height: 80vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: var(--white);
        }

        .hero-content h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .hero-content p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
        }

        /* --- PRODUCTS GRID --- */
        .section-title {
            text-align: center;
            margin: 4rem 0 2rem;
            font-size: 2.5rem;
            color: var(--text-dark);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 4rem;
        }

        .product-card {
            background: var(--white);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            transition: transform 0.3s;
        }

        .product-card:hover {
            transform: translateY(-5px);
        }

        .product-image {
            height: 300px;
            width: 100%;
            object-fit: cover;
        }

        .product-info {
            padding: 1.5rem;
            text-align: center;
        }

        .product-price {
            color: var(--primary-color);
            font-weight: bold;
            font-size: 1.2rem;
            margin: 0.5rem 0;
        }

        /* --- ABOUT SECTION --- */
        .about-section {
            background-color: var(--secondary-color);
            padding: 4rem 2rem;
            text-align: center;
        }

        .about-content {
            max-width: 800px;
            margin: 0 auto;
        }

        /* --- LEGAL SECTION (Privacy & Cookies) --- */
        .legal-section {
            background-color: #f9f9f9;
            padding: 4rem 2rem;
            border-top: 1px solid #eee;
        }

        .legal-container {
            max-width: 900px;
            margin: 0 auto;
            background: var(--white);
            padding: 3rem;
            border-radius: 8px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.05);
        }

        .legal-block {
            margin-bottom: 3rem;
            border-bottom: 1px solid #eee;
            padding-bottom: 2rem;
        }

        .legal-block:last-child {
            border-bottom: none;
        }

        .legal-block h3 {
            color: var(--primary-color);
            margin-bottom: 1rem;
            font-size: 1.8rem;
        }

        .legal-block p {
            margin-bottom: 1rem;
            color: var(--text-light);
            text-align: justify;
        }

        .legal-block ul {
            margin-left: 2rem;
            margin-bottom: 1rem;
            color: var(--text-light);
        }

        /* --- FOOTER --- */
        footer {
            background-color: #222;
            color: var(--white);
            padding: 3rem 2rem;
            text-align: center;
        }

        .footer-links {
            margin-bottom: 2rem;
        }

        .footer-links a {
            margin: 0 1rem;
            color: #aaa;
        }

        .footer-links a:hover {
            color: var(--white);
        }

        /* --- COOKIE BANNER --- */
        #cookie-banner {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            background-color: var(--white);
            box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
            padding: 1.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 2000;
            border-top: 4px solid var(--primary-color);
        }

        .cookie-text {
            font-size: 0.9rem;
            color: var(--text-dark);
        }

        .cookie-btn {
            background-color: var(--text-dark);
            color: var(--white);
            border: none;
            padding: 0.5rem 1.5rem;
            cursor: pointer;
            border-radius: 5px;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero-content h1 { font-size: 2.5rem; }
            .navbar { flex-direction: column; gap: 1rem; }
            #cookie-banner { flex-direction: column; text-align: center; gap: 1rem; }
        }
    </style>
    <!-- Importing Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700&family=Playfair+Display:wght@400;700&display=swap" rel="stylesheet">
</head>
<body>

    <!-- Header -->
    <header>
        <nav class="navbar">
            <div class="logo">LUMINA BEAUTY</div>
            <div class="nav-links">
                <a href="#home">Home</a>
                <a href="#shop">Shop</a>
                <a href="#about">Our Story</a>
                <a href="#legal">Legal & Privacy</a>
            </div>
            <a href="#" class="btn-primary">Cart (0)</a>
        </nav>
    </header>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Reveal Your Inner Glow</h1>
            <p>Cruelty-free, vegan, and scientifically formulated for every skin tone.</p>
            <a href="#shop" class="btn-primary">Shop The Collection</a>
        </div>
    </section>

    <!-- Products Section -->
    <section id="shop" class="container">
        <h2 class="section-title">Best Sellers</h2>
        <div class="product-grid">
            <!-- Product 1 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1620916566398-39f1143ab7be?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="Serum" class="product-image">
                <div class="product-info">
                    <h3>Velvet Silk Foundation</h3>
                    <p class="product-price">$34.00</p>
                    <a href="#" class="btn-primary" style="padding: 0.5rem 1rem; font-size: 0.9rem;">Add to Cart</a>
                </div>
            </div>
            <!-- Product 2 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1596462502278-27bfdd403348?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="Lipstick" class="product-image">
                <div class="product-info">
                    <h3>Rose Gold Matte Lipstick</h3>
                    <p class="product-price">$18.00</p>
                    <a href="#" class="btn-primary" style="padding: 0.5rem 1rem; font-size: 0.9rem;">Add to Cart</a>
                </div>
            </div>
            <!-- Product 3 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1512496015851-a90fb38ba796?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="Palette" class="product-image">
                <div class="product-info">
                    <h3>Sunset Eyeshadow Palette</h3>
                    <p class="product-price">$45.00</p>
                    <a href="#" class="btn-primary" style="padding: 0.5rem 1rem; font-size: 0.9rem;">Add to Cart</a>
                </div>
            </div>
            <!-- Product 4 -->
            <div class="product-card">
                <img src="https://images.unsplash.com/photo-1629198688000-71f23e745b6e?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60" alt="Mascara" class="product-image">
                <div class="product-info">
                    <h3>Volume Boost Mascara</h3>
                    <p class="product-price">$22.00</p>
                    <a href="#" class="btn-primary" style="padding: 0.5rem 1rem; font-size: 0.9rem;">Add to Cart</a>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about-section">
        <div class="about-content">
            <h2>Our Philosophy</h2>
            <br>
            <p>At Lumina Beauty, we believe that makeup is not a mask, but a tool for self-expression. Founded in 2023, our mission is to create high-performance cosmetics that are kind to your skin and the planet. We source our ingredients ethically and never test on animals. Every shade in our collection is designed to celebrate diversity and enhance your natural beauty.</p>
        </div>
    </section>

    <!-- Legal Section (Privacy & Cookies) -->
    <section id="legal" class="legal-section">
        <div class="container">
            <h2 class="section-title">Legal Information</h2>
            <div class="legal-container">
                
                <!-- Privacy Policy -->
                <div class="legal-block">
                    <h3>Privacy Policy</h3>
                    <p><strong>Last Updated: October 26, 2023</strong></p>
                    <p>At Lumina Beauty, accessible from www.luminabeauty.com, one of our main priorities is the privacy of our visitors. This Privacy Policy document contains types of information that is collected and recorded by Lumina Beauty and how we use it.</p>
                    
                    <h4>1. Log Files</h4>
                    <p>Lumina Beauty follows a standard procedure of using log files. These files log visitors when they visit websites. All hosting companies do this and a part of hosting services' analytics. The information collected by log files includes internet protocol (IP) addresses, browser type, Internet Service Provider (ISP), date and time stamp, referring/exit pages, and possibly the number of clicks.</p>

                    <h4>2. Cookies and Web Beacons</h4>
                    <p>Like any other website, Lumina Beauty uses 'cookies'. These cookies are used to store information including visitors' preferences, and the pages on the website that the visitor accessed or visited. The information is used to optimize the users' experience by customizing our web page content based on visitors' browser type and/or other information.</p>

                    <h4>3. Google DoubleClick DART Cookie</h4>
                    <p>Google is one of a third-party vendor on our site. It also uses cookies, known as DART cookies, to serve ads to our site visitors based upon their visit to www.website.com and other sites on the internet. However, visitors may choose to decline the use of DART cookies by visiting the Google ad and content network Privacy Policy at the following URL – <a href="#">https://policies.google.com/technologies/ads</a></p>

                    <h4>4. Our Advertising Partners</h4>
                    <p>Some of advertisers on our site may use cookies and web beacons. Our advertising partners are listed below. Each of our advertising partners has their own Privacy Policy for their policies on user data. For easier access, we hyperlinked to their Privacy Policies below.</p>
                    <ul>
                        <li>Google</li>
                        <li>Facebook</li>
                        <li>Instagram</li>
                    </ul>

                    <h4>5. Privacy Policies</h4>
                    <p>You may consult this list to find the Privacy Policy for each of the advertising partners of Lumina Beauty.</p>
                    <p>Third-party ad servers or ad networks use technologies like cookies, JavaScript, or Web Beacons that are used in their respective advertisements and links that appear on Lumina Beauty, which are sent directly to users' browser. They automatically receive your IP address when this occurs. These technologies are used to measure the effectiveness of their advertising campaigns and/or to personalize the advertising content that you see on websites that you visit.</p>

                    <h4>6. Third Party Privacy Policies</h4>
                   
