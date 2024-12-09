<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ern and Iso Podcast</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #1a237e, #f44336);
            color: #fff;
        }

        header {
            text-align: center;
            padding: 20px;
            background-image: url('https://upload.wikimedia.org/wikipedia/commons/4/41/Philadelphia_skyline_daytime.jpg');
            background-size: cover;
            color: #fff;
            text-shadow: 2px 2px 5px #000;
        }

        header img {
            width: 150px;
            border-radius: 50%;
        }

        header h1 {
            font-size: 3em;
            margin: 10px 0;
        }

        header p {
            font-size: 1.2em;
            margin: 5px 0;
        }

        nav {
            display: flex;
            justify-content: center;
            gap: 20px;
            background-color: #263238;
            padding: 10px;
        }

        nav a {
            text-decoration: none;
            color: #fff;
            font-weight: bold;
        }

        section {
            padding: 20px;
        }

        .about {
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
        }

        .about p {
            font-size: 1.2em;
        }

        footer {
            background-color: #212121;
            text-align: center;
            padding: 20px;
            color: #fff;
        }

        footer a {
            color: #f44336;
            text-decoration: none;
        }

        .socials {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 10px;
        }

        .socials a {
            color: #fff;
            font-size: 1.5em;
        }

        .btn {
            display: inline-block;
            background-color: #f44336;
            color: #fff;
            padding: 10px 15px;
            text-decoration: none;
            border-radius: 5px;
            margin: 10px;
        }

        #rss-episodes ul {
            list-style-type: none;
            padding: 0;
        }

        #rss-episodes li {
            margin: 10px 0;
        }

        #rss-episodes li a {
            color: #f44336;
            text-decoration: none;
            font-weight: bold;
        }

        #rss-episodes li a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <header>
        <img src="/mnt/data/51AC4260-80AE-4D67-BAB3-28EB83A62E15.jpg" alt="Ern and Iso Logo">
        <h1>Ern and Iso Podcast</h1>
        <p>If you don't know, now you know!!!!!</p>
    </header>

    <nav>
        <a href="#episodes">Episodes</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
    </nav>

    <section id="episodes">
        <h2>Episodes</h2>
        <p>Listen to us on your favorite platform!</p>
        <a class="btn" href="https://podcasts.apple.com/us/podcast/ern-and-iso/id1607761096" target="_blank">Apple Podcasts</a>
        <a class="btn" href="https://open.spotify.com/show/4ORo29HFhxs7SGQgZUv0He?si=3b5c9b6855d94c7b" target="_blank">Spotify Audio & Video</a>
        <iframe width="100%" height="315" src="https://www.youtube.com/embed/?listType=playlist&list=PL-your-playlist-id" title="YouTube Playlist" frameborder="0" allowfullscreen></iframe>
        <div id="rss-episodes">
            <h3>Latest Episodes</h3>
            <ul id="episode-list"></ul>
        </div>
    </section>

    <section id="about">
        <h2>About Us</h2>
        <div class="about">
            <p>Friends of over 30 years with different life experiences. Ern, married twice with 5 kids, and Iso, a bachelor with none, bring their unique perspectives to discuss entertainment, music, and life issues.</p>
        </div>
    </section>

    <section id="contact">
        <h2>Contact Us</h2>
        <p>Stay connected with us on social media or reach out directly!</p>
        <ul>
            <li>Email: <a href="mailto:isosince2022@gmail.com">isosince2022@gmail.com</a> | <a href="mailto:ern_iso@yahoo.com">ern_iso@yahoo.com</a></li>
            <li>Phone: <a href="tel:2675534953">(267) 553-4953</a></li>
        </ul>

        <div class="socials">
            <a href="https://facebook.com/ErnAndIso" target="_blank">Facebook</a>
            <a href="https://instagram.com/ern_and_iso" target="_blank">Instagram</a>
            <a href="https://twitter.com/Ern_and_Iso" target="_blank">Twitter</a>
            <a href="https://tiktok.com/@ern_and_iso1" target="_blank">TikTok</a>
        </div>

        <p>Support us on <a href="https://www.patreon.com/IsoVsTheWorld" target="_blank">Patreon</a></p>
    </section>

    <footer>
        <p>&copy; 2024 Ern and Iso Podcast. All rights reserved.</p>
    </footer>

    <script>
        const rssUrl = 'https://anchor.fm/s/80e670c8/podcast/rss';

        async function fetchEpisodes() {
            try {
                const response = await fetch(`https://api.rss2json.com/v1/api.json?rss_url=${encodeURIComponent(rssUrl)}`);
                const data = await response.json();

                if (data && data.items) {
                    const episodeList = document.getElementById('episode-list');
                    data.items.slice(0, 5).forEach(item => {
                        const li = document.createElement('li');
                        li.innerHTML = `<a href="${item.link}" target="_blank">${item.title}</a>`;
                        episodeList.appendChild(li);
                    });
                }
            } catch (error) {
                console.error('Error fetching RSS feed:', error);
            }
        }

        fetchEpisodes();
    </script>
</body>
</html>
