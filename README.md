<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube Unblocked</title>
    <style>
        body { font-family: Arial, sans-serif; background: #0f0f0f; color: #fff; margin: 0; padding: 20px; text-align: center; }
        input, button { padding: 10px; margin: 10px; font-size: 16px; }
        input { width: 60%; max-width: 500px; }
        button { background: #ff0000; color: white; border: none; cursor: pointer; }
        button:hover { background: #cc0000; }
        #player { max-width: 900px; margin: 20px auto; }
        iframe { width: 100%; height: 500px; border: none; }
    </style>
</head>
<body>
    <h1>YouTube Unblocked</h1>
    <p>Paste any YouTube link or search term</p>
    
    <input type="text" id="urlInput" placeholder="https://youtube.com/watch?v=VIDEO_ID or search term">
    <button onclick="loadVideo()">Go</button>
    
    <div id="player"></div>
    
    <script>
        function loadVideo() {
            const input = document.getElementById('urlInput').value.trim();
            const playerDiv = document.getElementById('player');
            playerDiv.innerHTML = '';
            
            if (!input) return;
            
            // Handle full URL
            if (input.includes('youtube.com') || input.includes('youtu.be')) {
                let videoId = '';
                if (input.includes('v=')) {
                    videoId = input.split('v=')[1].split('&')[0];
                } else if (input.includes('youtu.be/')) {
                    videoId = input.split('youtu.be/')[1].split('?')[0];
                }
                
                if (videoId) {
                    playerDiv.innerHTML = `
                        <iframe src="https://www.youtube-nocookie.com/embed/${videoId}?autoplay=1" 
                                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                                allowfullscreen></iframe>`;
                }
            } 
            // Search fallback
            else {
                const searchQuery = encodeURIComponent(input);
                playerDiv.innerHTML = `
                    <iframe src="https://www.youtube-nocookie.com/results?search_query=${searchQuery}" 
                            style="height: 600px;"></iframe>`;
            }
        }
        
        // Allow pressing Enter
        document.getElementById('urlInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') loadVideo();
        });
    </script>
</body>
</html>
