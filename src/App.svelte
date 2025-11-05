<script>
  const navItems = [{ label: "Home", href: "#home", page: "home" }];
  let currentPage = "home";

  // Initialize from hash on page load
  if (typeof window !== "undefined") {
    const hash = window.location.hash.slice(1);
    if (hash && ["home"].includes(hash)) {
      currentPage = hash;
    }
  }

  function navigate(page) {
    if (page) {
      currentPage = page;
      // Update URL hash
      if (typeof window !== "undefined") {
        window.location.hash = page;
      }
    }
  }

  // Listen for hash changes (back/forward buttons)
  if (typeof window !== "undefined") {
    window.addEventListener("hashchange", () => {
      const hash = window.location.hash.slice(1);
      if (hash && ["home"].includes(hash)) {
        currentPage = hash;
      } else if (!hash) {
        currentPage = "home";
      }
    });
  }
</script>

<header class="topbar">
  <div class="container">
    <div class="brand">
      <img src="/fosnhu_logo.png" alt="Furries of SNHU Logo" class="logo" />
      <h1>Furries of SNHU</h1>
    </div>
  </div>
  <nav class="navbar">
    <div class="container nav-inner">
      {#each navItems as item}
        <a
          class="nav-btn"
          href={item.href}
          rel="noopener noreferrer"
          on:click={() => navigate(item.page)}>{item.label}</a
        >
      {/each}
    </div>
  </nav>
</header>

<main class="container">
  {#if currentPage === "home"}
    <section class="content-block">
      <h2>Welcome</h2>
      <p>
        We are the Furries of SNHU! Whether you're online or in person, the
        FOSNHU community welcomes all SNHU furs!
      </p>
    </section>

    <div class="tiles-grid">
      <!-- Discord Widget Tile -->
      <div class="tile">
        <h3 class="tile-title">Join The Discord</h3>
        <div class="tile-content">
          <iframe
            src="https://discord.com/widget?id=963065508628926474&theme=dark"
            width="100%"
            height="500"
            allowtransparency="true"
            frameborder="0"
            sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts"
            title="Discord Server Widget"
          ></iframe>
          <p class="tile-note">
            Our discord server is SFW and welcoming for furs of all species,
            genders, orientations, sizes and anything else you can think of~
          </p>
        </div>
      </div>

      <!-- About Us Tile -->
      <div class="tile">
        <h3 class="tile-title">About Us</h3>
        <div class="tile-content">
          <p>
            The Furries of SNHU is a community of furries at Southern New
            Hampshire University. We're
            <strong> not an offical student organization </strong>
            , but we are a community of furries at SNHU.
          </p>
          <p>
            If you're new to the fandom or a long time member, everyone is
            welcome!
          </p>
          <p>
            Connect with us on Discord, come to our meetups (Online and On
            Campus), and be part of the SNHU furry community!
          </p>
        </div>
      </div>
    </div>
  {/if}
</main>
