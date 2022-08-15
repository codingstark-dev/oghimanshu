<script type="ts">
  import cringe from "../lib/cringe.json";
  import html2canvas from "html2canvas";
  import { saveAs } from "file-saver";

  let random = Math.floor(Math.random() * cringe.length);
  function takess() {
    // if (typeof window !== 'undefined') {
    html2canvas(document.getElementById("quotes") as any).then((canvas) => {
      canvas.toBlob(function (blob : any) {
        saveAs(blob  , `og.himanshu.dev ${random * 10}.png`);
      });

      // document.body.appendChild(canvas);
    });
  }

  $: reload();
  function reload() {
    if (random != Math.floor(Math.random() * cringe.length)) {
      random = Math.floor(Math.random() * cringe.length);
    } else {
      reload();
    }
    // random = Math.floor(Math.random() * cringe.length);
    // window.location.reload();
  }
  // }

</script>

<li class="link-card" id="quotes">
  <a>
    <h2>
      {cringe[random].quotes}
    </h2>
    <p class="font-semibold">
      <span>-</span> <strike>{cringe[random].author}</strike> Himanshu Maurya
    </p>
  </a><button on:click={reload}
    ><svg class="w-6" viewBox="0 0 24 24">
      <path
        fill="currentColor"
        d="M12 20q-3.35 0-5.675-2.325Q4 15.35 4 12q0-3.35 2.325-5.675Q8.65 4 12 4q1.725 0 3.3.713q1.575.712 2.7 2.037V4h2v7h-7V9h4.2q-.8-1.4-2.187-2.2Q13.625 6 12 6Q9.5 6 7.75 7.75T6 12q0 2.5 1.75 4.25T12 18q1.925 0 3.475-1.1T17.65 14h2.1q-.7 2.65-2.85 4.325Q14.75 20 12 20Z"
      />
    </svg></button
  >
</li>
<button on:click={takess} class="w-full font-bold" >

  <p class="instructions">Download Image</p>
</button>


<style>
  .instructions {
    display: flex;
    texct-align: center;
    justify-content: center;
    line-height: 1.6;
    margin: 1rem 0;
    background: #4f39fa;
    padding: 1rem;
    border-radius: 0.4rem;
    color: var(--color-bg);
  }

  .instructions code {
    font-size: 0.875em;
    border: 0.1em solid var(--color-border);
    border-radius: 4px;
    padding: 0.15em 0.25em;
  }

  :root {
    --link-gradient: linear-gradient(
      45deg,
      #4f39fa,
      #da62c4 30%,
      var(--color-border) 60%
    );
  }
  div#ss {
    margin: 10px;
  }
  .link-card {
    list-style: none;
    display: flex;
    padding: 0.15rem;
    background-image: var(--link-gradient);
    background-size: 400%;
    border-radius: 0.5rem;
    background-position: 100%;
    transition: background-position 0.6s cubic-bezier(0.22, 1, 0.36, 1);
  }

  .link-card > a {
    width: 100%;
    text-decoration: none;
    line-height: 1.4;
    padding: 1em 1.3em;
    border-radius: 0.35rem;
    color: var(--text-color);
    background-color: white;
    opacity: 0.8;
  }

  h2 {
    margin: 0;
    transition: color 0.6s cubic-bezier(0.22, 1, 0.36, 1);
  }

  p {
    margin-top: 0.75rem;
    margin-bottom: 0;
  }

  h2 span {
    display: inline-block;
    transition: transform 0.3s cubic-bezier(0.22, 1, 0.36, 1);
  }

  .link-card {
    background-position: 0;
  }

  .link-card h2 {
    color: #4f39fa;
  }

  .link-card h2 span {
    will-change: transform;
    transform: translateX(2px);
  }
</style>
