---
layout: page
title: smolhyper
permalink: /smolhyper/
description: Twitch chat commands and runtime status for SmolHyper.
nav: true
nav_order: 4
_styles: |
  .smolhyper-page {
    --smol-bg: #15110d;
    --smol-panel: rgba(255, 248, 237, 0.08);
    --smol-panel-strong: rgba(255, 248, 237, 0.12);
    --smol-line: rgba(255, 248, 237, 0.18);
    --smol-text: #f7efe4;
    --smol-muted: #c7bba8;
    --smol-accent: #e58a2d;
    --smol-good: #95d5a6;
    --smol-ink: #251708;
    color: var(--smol-text);
    margin-top: 1.25rem;
  }

  .smolhyper-stage {
    position: relative;
    overflow: hidden;
    border: 1px solid var(--smol-line);
    background:
      radial-gradient(circle at 15% 10%, rgba(229, 138, 45, 0.28), transparent 30%),
      radial-gradient(circle at 82% 0%, rgba(149, 213, 166, 0.12), transparent 34%),
      linear-gradient(135deg, #1d150e 0%, var(--smol-bg) 58%, #0f0f0f 100%);
    box-shadow: 0 24px 70px rgba(0, 0, 0, 0.28);
    padding: clamp(1.35rem, 4vw, 2.75rem);
  }

  .smolhyper-stage::before {
    content: "";
    position: absolute;
    inset: 0;
    pointer-events: none;
    background-image:
      linear-gradient(rgba(255, 255, 255, 0.035) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255, 255, 255, 0.035) 1px, transparent 1px);
    background-size: 32px 32px;
    mask-image: linear-gradient(180deg, black, transparent 90%);
  }

  .smolhyper-hero,
  .smolhyper-grid,
  .smolhyper-actions {
    position: relative;
    z-index: 1;
  }

  .smolhyper-hero {
    max-width: 44rem;
  }

  .smolhyper-hero h2 {
    color: var(--smol-text);
    font-family: Georgia, "Times New Roman", serif;
    font-size: clamp(2.7rem, 8vw, 5.4rem);
    line-height: 0.94;
    margin: 0;
  }

  .smolhyper-hero p {
    color: var(--smol-muted);
    font-size: 1.05rem;
    line-height: 1.65;
    margin: 1rem 0 0;
  }

  .smolhyper-actions {
    align-items: center;
    display: flex;
    flex-wrap: wrap;
    gap: 0.75rem;
    margin: 1.35rem 0 1.75rem;
  }

  .smolhyper-button {
    align-items: center;
    background: var(--smol-accent);
    border: 1px solid var(--smol-accent);
    color: var(--smol-ink);
    display: inline-flex;
    font-weight: 700;
    min-height: 42px;
    padding: 0 1rem;
    text-decoration: none;
  }

  .smolhyper-button.secondary {
    background: transparent;
    border-color: var(--smol-line);
    color: var(--smol-text);
  }

  .smolhyper-grid {
    display: grid;
    gap: 1rem;
    grid-template-columns: minmax(0, 0.8fr) minmax(0, 1.2fr);
  }

  .smolhyper-panel {
    background: linear-gradient(180deg, var(--smol-panel), var(--smol-panel-strong));
    border: 1px solid var(--smol-line);
    padding: 1rem;
  }

  .smolhyper-panel h3 {
    color: var(--smol-text);
    font-size: 1.15rem;
    margin: 0 0 0.85rem;
  }

  .smolhyper-status-list {
    display: grid;
    gap: 0.65rem;
  }

  .smolhyper-status-item,
  .smolhyper-command {
    background: rgba(0, 0, 0, 0.18);
    border: 1px solid var(--smol-line);
    padding: 0.85rem;
  }

  .smolhyper-status-item span {
    color: var(--smol-muted);
    display: block;
    font-size: 0.75rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }

  .smolhyper-status-item strong {
    color: var(--smol-text);
    display: block;
    font-size: 1.1rem;
    margin-top: 0.25rem;
  }

  .smolhyper-command-list {
    display: grid;
    gap: 0.75rem;
  }

  .smolhyper-trigger {
    color: var(--smol-good);
    font-family: "Courier New", monospace;
    font-size: 1rem;
    margin: 0 0 0.4rem;
  }

  .smolhyper-response {
    color: var(--smol-muted);
    line-height: 1.5;
    margin: 0;
  }

  @media (max-width: 760px) {
    .smolhyper-grid {
      grid-template-columns: 1fr;
    }
  }
---

<section class="smolhyper-page">
  <div class="smolhyper-stage">
    <div class="smolhyper-hero">
      <h2>SmolHyper is listening.</h2>
      <p>
        Public Twitch chat commands for the SmolHyper bot. This page lives on SnowfallDev, while
        the always-on chat service runs safely in the cloud.
      </p>
    </div>

    <div class="smolhyper-actions">
      <a class="smolhyper-button" href="https://www.twitch.tv/lilmackthesnack" target="_blank" rel="noreferrer">Open test channel</a>
      <a class="smolhyper-button secondary" href="https://abstractbot.onrender.com/admin" target="_blank" rel="noreferrer">Mod console</a>
    </div>

    <div class="smolhyper-grid">
      <aside class="smolhyper-panel">
        <h3>Runtime</h3>
        <div class="smolhyper-status-list">
          <div class="smolhyper-status-item">
            <span>Status</span>
            <strong id="smolhyper-health">Loading</strong>
          </div>
          <div class="smolhyper-status-item">
            <span>Storage</span>
            <strong id="smolhyper-storage">Checking</strong>
          </div>
          <div class="smolhyper-status-item">
            <span>Commands</span>
            <strong id="smolhyper-count">Checking</strong>
          </div>
        </div>
      </aside>

      <section class="smolhyper-panel">
        <h3>Active Commands</h3>
        <div id="smolhyper-commands" class="smolhyper-command-list">
          <article class="smolhyper-command">
            <p class="smolhyper-response">Loading command records...</p>
          </article>
        </div>
      </section>
    </div>
  </div>
</section>

<script>
  (() => {
    const apiBase = "https://abstractbot.onrender.com";
    const commandsElement = document.querySelector("#smolhyper-commands");
    const healthElement = document.querySelector("#smolhyper-health");
    const storageElement = document.querySelector("#smolhyper-storage");
    const countElement = document.querySelector("#smolhyper-count");

    const escapeHtml = (value) =>
      String(value ?? "").replace(/[&<>"']/g, (char) => ({
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        '"': "&quot;",
        "'": "&#039;",
      })[char]);

    const renderCommands = (commands) => {
      if (!commands.length) {
        commandsElement.innerHTML = `
          <article class="smolhyper-command">
            <p class="smolhyper-response">No public commands have been published yet.</p>
          </article>
        `;
        return;
      }

      commandsElement.innerHTML = commands
        .map((command) => `
          <article class="smolhyper-command">
            <p class="smolhyper-trigger">${escapeHtml(command.trigger)}</p>
            <p class="smolhyper-response">${escapeHtml(command.response)}</p>
          </article>
        `)
        .join("");
    };

    Promise.all([
      fetch(`${apiBase}/api/health`).then((response) => response.json()),
      fetch(`${apiBase}/api/commands`).then((response) => response.json()),
    ])
      .then(([health, commandPayload]) => {
        const commands = commandPayload.commands ?? [];
        healthElement.textContent = health.ok ? "Online" : "Degraded";
        storageElement.textContent = health.storageBackend ?? "Unknown";
        countElement.textContent = `${health.commandCount ?? commands.length} active`;
        renderCommands(commands);
      })
      .catch((error) => {
        healthElement.textContent = "Unavailable";
        storageElement.textContent = "Unknown";
        countElement.textContent = "Unknown";
        commandsElement.innerHTML = `
          <article class="smolhyper-command">
            <p class="smolhyper-response">
              SmolHyper data could not be loaded yet: ${escapeHtml(error.message)}
            </p>
          </article>
        `;
      });
  })();
</script>
