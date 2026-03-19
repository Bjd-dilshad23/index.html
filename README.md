<script>
    // Pehle se behtar Movement Logic
    let speed = 5;
    function updatePlayer() {
        player.x += moveX * speed;
        player.y += moveY * speed;

        // Screen se bahar na jaye uske liye:
        if(player.x < 0) player.x = 0;
        if(player.y < 0) player.y = 0;
        if(player.x > canvas.width - player.size) player.x = canvas.width - player.size;
        if(player.y > canvas.height - player.size) player.y = canvas.height - player.size;
    }

    // Bhojpuri Voice Command (Testing ke liye)
    function bolBhojpuri(text) {
        let utterance = new SpeechSynthesisUtterance(text);
        utterance.lang = 'hi-IN'; // Bhojpuri ke liye Hindi accent best kaam karta hai
        window.speechSynthesis.speak(utterance);
    }

    // Jab game chalu ho toh ye bolega
    window.onload = () => {
        bolBhojpuri("Pranaam! Patna Metro Station mein raua swagat ba.");
    };
</script>





