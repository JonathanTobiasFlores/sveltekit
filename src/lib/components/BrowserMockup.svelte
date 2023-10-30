<script>
  let text = "console.log('Hello World!')";
  let displayText = '';
  let index = 0;

  const typeText = () => {
    if (index < text.length) {
      displayText += text.charAt(index);
      index++;
      setTimeout(typeText, 100);
    }
  };

  const restartTyping = () => {
    displayText = '';
    index = 0;
    typeText();
  };

  typeText();
  setInterval(restartTyping, 10000);
</script>

<style>
  .typing-effect {
    display: inline-block;
    font-family: monospace;
    white-space: pre;
    user-select: none;
  }

  .typing-cursor {
    display: inline-block;
    width: 2px;
    height: 1.4em;
    background-color: #ffffff;
    vertical-align: middle;
    animation: blink 0.7s step-end infinite;
  }

  @keyframes blink {
    0%, 50% { opacity: 1 }
    50.1%, 100% { opacity: 0 }
  }
</style>

<div class="mockup-browser border bg-base-300">
  <div class="mockup-browser-toolbar">
    <div class="input">
      <a href="https://github.com/jonathantobiasflores" target="_blank" rel="noopener noreferrer">
        https://github.com/jonathantobiasflores
      </a>
    </div>
  </div>
  <div class="flex justify-center px-4 py-16 bg-base-200">
    <div class="typing-effect" contenteditable="false">
      {displayText}<div class="typing-cursor"></div>
    </div>    
  </div>
</div>
