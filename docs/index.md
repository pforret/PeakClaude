---
title: "Is it OK now?"
---
# Are we in Claude Code peak hours right now?

<div id="peak-clock" style="text-align:center; padding: 2rem 1rem; margin: 1.5rem 0; border-radius: 12px; font-family: inherit;">
  <div id="peak-status" style="font-size: 2.5rem; font-weight: 700; margin-bottom: 0.5rem;"></div>
  <div id="peak-label" style="font-size: 1.2rem; margin-bottom: 1.5rem;"></div>
  <div style="display: flex; justify-content: center; gap: 2rem; flex-wrap: wrap;">
    <div>
      <div style="font-size: 0.8rem; text-transform: uppercase; letter-spacing: 0.1em; opacity: 0.7;">Your time</div>
      <div id="local-time" style="font-size: 1.4rem; font-weight: 600; font-variant-numeric: tabular-nums;"></div>
    </div>
    <div>
      <div style="font-size: 0.8rem; text-transform: uppercase; letter-spacing: 0.1em; opacity: 0.7;">Pacific Time</div>
      <div id="pt-time" style="font-size: 1.4rem; font-weight: 600; font-variant-numeric: tabular-nums;"></div>
    </div>
  </div>
  <div id="peak-next" style="margin-top: 1rem; font-size: 0.95rem; opacity: 0.8;"></div>
</div>

**Peak hours:** Weekdays 5 AM - 11 AM PT / 1 PM - 7 PM GMT | [Full schedule](schedule.md) | [Advice](advice.md)

<script>
(function () {
  const PEAK_START = 5;  // 5 AM PT
  const PEAK_END = 11;   // 11 AM PT (exclusive)
  const ptFormat = new Intl.DateTimeFormat("en-US", {
    timeZone: "America/Los_Angeles",
    hour: "2-digit", minute: "2-digit", second: "2-digit",
    hour12: false
  });
  const localFormat = new Intl.DateTimeFormat("en-US", {
    hour: "2-digit", minute: "2-digit", second: "2-digit",
    hour12: false
  });

  function getPtParts(date) {
    const parts = new Intl.DateTimeFormat("en-US", {
      timeZone: "America/Los_Angeles",
      hour: "numeric", minute: "numeric", weekday: "short",
      hour12: false
    }).formatToParts(date);
    const hour = parseInt(parts.find(p => p.type === "hour").value);
    const dayStr = parts.find(p => p.type === "weekday").value;
    const weekdays = ["Mon", "Tue", "Wed", "Thu", "Fri"];
    const isWeekday = weekdays.includes(dayStr);
    return { hour, isWeekday, dayStr };
  }

  function isPeak(date) {
    const { hour, isWeekday } = getPtParts(date);
    return isWeekday && hour >= PEAK_START && hour < PEAK_END;
  }

  function getNextTransition(date) {
    const { hour, isWeekday, dayStr } = getPtParts(date);
    if (isWeekday && hour >= PEAK_START && hour < PEAK_END) {
      // Currently peak -> ends at PEAK_END today
      const minsLeft = (PEAK_END - hour - 1) * 60 + (60 - parseInt(ptFormat.format(date).split(":")[1]));
      return { label: "Peak ends in", minutes: minsLeft };
    }
    // Find next peak start
    let hoursUntil = 0;
    if (isWeekday && hour < PEAK_START) {
      hoursUntil = PEAK_START - hour;
      const mins = parseInt(ptFormat.format(date).split(":")[1]);
      return { label: "Next peak in", minutes: hoursUntil * 60 - mins };
    }
    // After peak on weekday, or weekend — find next weekday 5 AM
    const days = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];
    const dayIndex = days.indexOf(dayStr);
    let daysUntilMon;
    if (dayIndex === 0) daysUntilMon = 1;       // Sun -> Mon
    else if (dayIndex === 6) daysUntilMon = 2;   // Sat -> Mon
    else if (dayIndex === 5 && hour >= PEAK_END) daysUntilMon = 3; // Fri after peak -> Mon
    else daysUntilMon = 1; // weekday after peak -> next day
    // But if it's Fri after peak, next peak is Mon
    // If weekday after peak, next peak is tomorrow
    const minsToday = (24 - hour) * 60 - parseInt(ptFormat.format(date).split(":")[1]);
    const totalMins = minsToday + (daysUntilMon - 1) * 24 * 60 + PEAK_START * 60;
    return { label: "Next peak in", minutes: totalMins };
  }

  function formatDuration(mins) {
    if (mins < 0) mins = 0;
    const h = Math.floor(mins / 60);
    const m = mins % 60;
    if (h > 24) {
      const d = Math.floor(h / 24);
      const rh = h % 24;
      return `${d}d ${rh}h`;
    }
    if (h > 0) return `${h}h ${m}m`;
    return `${m}m`;
  }

  function update() {
    const now = new Date();
    const peak = isPeak(now);
    const clockEl = document.getElementById("peak-clock");
    const statusEl = document.getElementById("peak-status");
    const labelEl = document.getElementById("peak-label");
    const localEl = document.getElementById("local-time");
    const ptEl = document.getElementById("pt-time");
    const nextEl = document.getElementById("peak-next");

    if (peak) {
      clockEl.style.background = "linear-gradient(135deg, #b71c1c 0%, #e53935 100%)";
      clockEl.style.color = "#fff";
      statusEl.textContent = "🔴 PEAK HOURS";
      labelEl.textContent = "Claude Code session limits are tighter right now";
    } else {
      clockEl.style.background = "linear-gradient(135deg, #1b5e20 0%, #43a047 100%)";
      clockEl.style.color = "#fff";
      statusEl.textContent = "🟢 OFF-PEAK";
      labelEl.textContent = "Full session limits available";
    }

    localEl.textContent = localFormat.format(now);
    ptEl.textContent = ptFormat.format(now);

    const next = getNextTransition(now);
    nextEl.textContent = `${next.label} ~${formatDuration(next.minutes)}`;
  }

  update();
  setInterval(update, 10000);
})();
</script>
