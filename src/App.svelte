<script>
  var wordlist = [];
  var password = "...";
  var dicecolor = "color: #FFF";

  function generatePassword(wait, num) {
    password = "Generating...";
    dicecolor = "color: #00AEFF";

    fetch(`https://random-word-api.herokuapp.com/word?number=${num}`)
      .then((response) => response.json())
      .then((data) => (wordlist = data));

    setTimeout(() => {
      wordlist = wordlist.join(" ");
      wordlist = wordlist.replace(/(^\w{1})|(\s+\w{1})/g, (letter) =>
        letter.toUpperCase()
      );
      wordlist = wordlist.replace(/ /g, "");
      password = wordlist;
      dicecolor = "color: #82C91E";
    }, wait);
  }
</script>

<svelte:head>
  <script
    src="https://kit.fontawesome.com/fb74415b25.js"
    crossorigin="anonymous"></script>
  <link rel="preconnect" href="https://fonts.gstatic.com" />
  <link
    href="https://fonts.googleapis.com/css2?family=Inter&display=swap"
    rel="stylesheet"
  />
</svelte:head>

<body>
  <div class="container">
    <div class="dice" style={dicecolor}>
      <i class="far fa-dice" />
    </div>
    <h1 class="title">Dicepass</h1>
    <h3 class="subtitle">Super-secure diceware passwords!sdfsdf</h3>
    <div class="strength-container">
      <button
        class="strength-button one"
        on:click={() => generatePassword(2000, 5)}
      >
        Tough
      </button>
      <button
        class="strength-button two"
        on:click={() => generatePassword(4000, 7)}
      >
        Strong
      </button>
      <button
        class="strength-button three"
        on:click={() => generatePassword(6000, 9)}
      >
        Max
      </button>
    </div>
    <h2 class="password">{password}</h2>
  </div>
  <div class="footer"><p>By Mark Zhou</p></div>
  <a
    href="https://github.com/gradientmz/dicepass"
    class="github-corner"
    aria-label="View source on GitHub"
    ><svg
      width="80"
      height="80"
      viewBox="0 0 250 250"
      style="fill:#fff; color:#151513; position: absolute; top: 0; border: 0; right: 0;"
      aria-hidden="true"
      ><path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z" /><path
        d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2"
        fill="currentColor"
        style="transform-origin: 130px 106px;"
        class="octo-arm"
      /><path
        d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z"
        fill="currentColor"
        class="octo-body"
      /></svg
    ></a
  ><style>
    .github-corner:hover .octo-arm {
      animation: octocat-wave 560ms ease-in-out;
    }
    @keyframes octocat-wave {
      0%,
      100% {
        transform: rotate(0);
      }
      20%,
      60% {
        transform: rotate(-25deg);
      }
      40%,
      80% {
        transform: rotate(10deg);
      }
    }
    @media (max-width: 500px) {
      .github-corner:hover .octo-arm {
        animation: none;
      }
      .github-corner .octo-arm {
        animation: octocat-wave 560ms ease-in-out;
      }
    }
  </style>
</body>

<style>
  body {
    font-family: "Inter", sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;

    background-image: url("https:/svgshare.com/i/Uyr.svg");
  }
  h2 {
    color: white;
    text-align: center;
  }
  .dice {
    text-align: center;
    font-size: 4rem;
    color: #00aeff;
    transition: 1s;
  }
  .strength-container {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .strength-button {
    border-radius: 0.5rem;
    font-size: larger;
    padding: 0.5rem 0.75rem;
    margin: 0.25rem;
    font-weight: bold;
  }
  .title {
    color: white;
    font-size: 3rem;
    margin: 0.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .subtitle {
    color: white;
    text-align: center;
    margin: 0rem 1rem 2rem 1rem;
    font-weight: normal;
    color: white;
  }
  .password {
    font-weight: bold;
    background-color: black;
    border: 3px solid white;
    border-radius: 0.5rem;
    padding: 0.75rem;
    overflow-wrap: break-word;
    width: 70vw;
    max-width: 90rem;
    margin: 1.5rem auto;
  }
  .footer {
    padding: 5px;
    bottom: 0;
    position: fixed;
    width: 100%;
    left: -5px;
    text-align: center;
    color: gray;
  }
</style>
