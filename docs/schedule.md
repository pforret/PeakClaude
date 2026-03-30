---
description: Weekly schedule of Claude Code peak and off-peak hours with interactive grid and time zone reference.
---

# Weekly Schedule

<div id="peak-schedule" style="max-width: 600px; margin: 2rem auto;">
  <div id="week-grid" style="display: grid; grid-template-columns: auto repeat(24, 1fr); gap: 2px; font-size: 0.7rem;"></div>
  <div style="display: flex; justify-content: center; gap: 1.5rem; margin-top: 0.75rem; font-size: 0.8rem;">
    <span>🔴 Peak hours</span>
    <span>🟢 Off-peak</span>
    <span>▶ Now</span>
  </div>
</div>

## Peak hours by time zone

|              | Hours (Pacific)        | Hours (GMT/UTC)        | Hours (CET)            |
|--------------|------------------------|------------------------|------------------------|
| **Peak**     | Weekdays 5 AM - 11 AM | Weekdays 1 PM - 7 PM  | Weekdays 2 PM - 8 PM  |
| **Off-peak** | All other times        | All other times        | All other times        |

- Weekends are entirely off-peak
- Weekly token limits stay the same — only the per-session distribution changes
- ~7% of users hit session limits they wouldn't have before, particularly on Pro tiers

## Daily breakdown

| Day       | 00-05 PT | 05-11 PT   | 11-24 PT |
|-----------|----------|------------|----------|
| Monday    | Off-peak | **Peak**   | Off-peak |
| Tuesday   | Off-peak | **Peak**   | Off-peak |
| Wednesday | Off-peak | **Peak**   | Off-peak |
| Thursday  | Off-peak | **Peak**   | Off-peak |
| Friday    | Off-peak | **Peak**   | Off-peak |
| Saturday  | Off-peak | Off-peak   | Off-peak |
| Sunday    | Off-peak | Off-peak   | Off-peak |

**Total peak hours per week:** 30 hours (out of 168)

See [Practical Advice](advice.md) for tips on organizing your work around these hours.

<script>
(function () {
  const PEAK_START = 5;
  const PEAK_END = 11;
  const ptFormat = new Intl.DateTimeFormat("en-US", {
    timeZone: "America/Los_Angeles",
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
    return { hour, dayStr };
  }

  function buildWeekGrid() {
    const grid = document.getElementById("week-grid");
    if (!grid) return;
    grid.innerHTML = "";
    const days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
    const corner = document.createElement("div");
    corner.style.cssText = "font-weight:600; padding: 2px 4px;";
    grid.appendChild(corner);
    for (let h = 0; h < 24; h++) {
      const cell = document.createElement("div");
      cell.style.cssText = "text-align:center; font-size:0.55rem; opacity:0.6;";
      cell.textContent = h % 6 === 0 ? h : "";
      grid.appendChild(cell);
    }
    const now = new Date();
    const { hour: nowHour, dayStr: nowDay } = getPtParts(now);

    days.forEach((day, di) => {
      const label = document.createElement("div");
      label.style.cssText = "font-weight:600; padding: 2px 4px; display:flex; align-items:center;";
      label.textContent = day;
      grid.appendChild(label);
      const isWeekday = di < 5;
      for (let h = 0; h < 24; h++) {
        const cell = document.createElement("div");
        const peak = isWeekday && h >= PEAK_START && h < PEAK_END;
        const isCurrent = nowDay === day && nowHour === h;
        let bg = peak ? "#e53935" : "#43a047";
        let opacity = peak ? "0.85" : "0.3";
        if (isCurrent) {
          bg = peak ? "#ff1744" : "#00e676";
          opacity = "1";
          cell.style.border = "2px solid white";
          cell.style.boxSizing = "border-box";
        }
        cell.style.cssText += `background:${bg}; opacity:${opacity}; border-radius:2px; min-height:18px; position:relative; display:flex; align-items:center; justify-content:center;`;
        if (isCurrent) {
          cell.style.border = "2px solid #fff";
          cell.textContent = "▶";
          cell.style.fontSize = "0.5rem";
          cell.style.color = "#fff";
        }
        grid.appendChild(cell);
      }
    });
  }

  buildWeekGrid();
  setInterval(buildWeekGrid, 60000);
})();
</script>
