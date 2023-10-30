<script>
  import { onMount } from 'svelte';
  let text = 'Fetching quote...';
  let displayText = '';
  let index = 0;

  const typeText = () => {
    if (index < text.length) {
      displayText += text.charAt(index);
      index++;
      setTimeout(typeText, 80);
    }
  };

  const fetchGamingQuote = async () => {
    try {
      const response = await fetch('https://api.quotable.io/random');
      const data = await response.json();
      text = `"${data.content}" — ${data.author}`;
      displayText = '';
      index = 0;
      typeText();
    } catch (error) {
      console.error('Error fetching quote:', error);
      text = 'Failed to fetch quote.';
      displayText = '';
      index = 0;
      typeText();
    }
  };

  onMount(() => {
    fetchGamingQuote();
    setInterval(fetchGamingQuote, 20000);
  });
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
