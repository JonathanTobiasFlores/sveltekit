<script>
  let text = "console.log('Hello World!')";
  let displayText = '';
  let index = 0;

  const typeText = () => {
    if (index < text.length) {
      displayText += text.charAt(index);
      index++;
      setTimeout(typeText, 100); // Adjust speed as necessary
    }
  };

  const restartTyping = () => {
    displayText = '';
    index = 0;
    typeText();
  };

  typeText();
  setInterval(restartTyping, 10000); // Restart every 10 seconds
</script>

<style>
  .typing-effect {
    display: inline-block;
    font-family: monospace;
    white-space: pre;
  }

  .typing-cursor {
    border-right: 2px solid #000;
    animation: blink 0.7s infinite;
  }

  @keyframes blink {
    from, to { border-color: transparent; }
    50% { border-color: black; }
  }
</style>

<div class="mockup-browser border bg-base-300">
  <div class="mockup-browser-toolbar">
    <div class="input">https://github.com/jonathantobiasflores</div>
  </div>
  <div class="flex justify-center px-4 py-16 bg-base-200">
    <div class="typing-effect">
      {displayText}<div class="typing-cursor"></div>
    </div>
  </div>
</div>
