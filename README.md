# 🚀 Elite Dangerous Mining Calculator

> **Realistic laser mining route optimizer with live market data**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Elite Dangerous](https://img.shields.io/badge/Elite%20Dangerous-Mining-orange)](https://www.elitedangerous.com/)

---

## 📖 What Is This?

A Python tool that calculates the **most profitable laser mining routes** in Elite Dangerous with **realistic time estimates** that match actual gameplay.

### ✨ Key Features

- 🔍 **Live Data**: Fetches real-time hotspot locations and commodity prices from EDTools.cc & EDSM
- ⏱️ **Realistic Times**: Accounts for prospecting, positioning, and collection delays (not just theoretical extraction)
- 💰 **Profit Optimization**: Calculates Cr/h with bulk sales tax, limpet costs, and travel time
- 🎯 **Three Mining Modes**: Mapped routes, unmapped hotspots, or beginner-friendly calculations
- 📊 **Top 5 Routes**: Automatically ranks the best routes from your current system

---

## 🎮 Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/vivladius/elite-mining-calculator.git
cd elite-mining-calculator

# Install dependencies
pip install -r requirements.txt

# Run the calculator
python mining_calc.py
```

### Usage

1. **Enter your current system** (e.g., "Sol", "Deciat")
2. **Select mining mode**:
   - **Mapped Routes** (2x time multiplier) - Following mining maps/guides
   - **Unmapped Hotspots** (3.5x multiplier) - Random prospecting (recommended)
   - **Beginner** (5x multiplier) - Still learning techniques
3. **Review top 5 routes** with profit, distance, and time estimates

---

## 📸 Example Output

```
======================================================================
ELITE DANGEROUS LASER MINING OPTIMIZER v3.0
======================================================================

Ship: MU-18A Asp Miner
Cargo: 96t | Jump Range: 26.87 LY (laden)
Lasers: 2x | Collectors: 2x

Enter your current system (default=Sol): Deciat
✅ Located system: Deciat

======================================================================
🏆 TOP 5 LASER MINING ROUTES (REALISTIC Cr/h)
======================================================================

#1: PLATINUM
   ⛏️  Mine at: Omicron Capricorni B
   🛒 Sell at: BD+05 4440 / Snyder Terminal [Pad: L]
   💰 Price: 285,432 Cr/t | Demand: 15,823 | Data: FRESH
   📍 Distance: 42.3 LY to mine + 18.7 LY to sell = 61.0 LY
   ⚙️  Pure extraction: 6.5 min @ 14.77 t/min
   ⏱️  REALISTIC mining: 22.8 min @ 4.21 t/min
   🚀 Travel: 8.2 min
   💎 Profit: 26,891,472 Cr → ⚡ 52,012,338 Cr/h (tax: 100%)
```

---

## 🔧 Configuration

### Default Ship: Asp Explorer

```python
SHIP = ShipProfile(
    name="MU-18A Asp Miner",
    cargo_tons=96,
    jump_range_ly=26.87,  # Laden
    jump_time_min=1.5,     # Per jump (includes FSD charge + cooldown)
    collector_controllers=2,
    num_lasers=2,
    ship_value=21_598_088
)
```

**To use a different ship**: Edit the `SHIP` variable in `mining_calc.py`

### Game Mechanics

```python
GameConfig(
    prospector_bonus=3.5,              # A-rated prospector (verified)
    laser_mining_rate_per_laser=2.5,   # tons/min (medium laser)
    limpet_collection_rate=2.8,        # tons/min per controller
    mining_downtime_factor=0.85,       # 15% time lost to repositioning
    limpet_loss_rate=0.10,             # 10% limpets destroyed
    time_multiplier_unmapped=3.5       # Real gameplay overhead
)
```

---

## 🧪 How It Works

### 1. Fetch Live Data
- **Hotspots**: Mining ring locations from EDTools.cc
- **Prices**: Station buy prices and demand from community data
- **Coordinates**: System distances from EDSM API

### 2. Calculate Routes
For each hotspot + buyer combination:
- ✅ **Distance**: 3D Euclidean calculation
- ✅ **Travel time**: Jumps + docking overhead
- ✅ **Mining time**: Theoretical extraction × realistic multiplier
- ✅ **Limpet costs**: With 10% loss rate
- ✅ **Bulk tax penalty**: When selling >25% of station demand
- ✅ **Profit per hour**: Revenue - costs ÷ cycle time

### 3. Rank & Display
Top 5 routes sorted by Cr/h

---

## ❓ FAQ

### Why are the times different from other tools?

Most calculators use **theoretical extraction rates** (pure laser + collection speed). This tool adds **realistic multipliers** for:
- Prospecting asteroids (finding good ones)
- Positioning and maneuvering
- Fragment collection delays
- Refinery management

**Result**: Times that match actual player experiences

### What's the difference between extraction time and realistic mining time?

- **Extraction time**: Pure laser + collection efficiency (6.5 min)
- **Realistic mining time**: Includes prospecting overhead (22.8 min)
- **Multiplier**: Depends on mode (2x mapped, 3.5x unmapped, 5x beginner)

### Can I use a different ship?

Yes! Edit the `SHIP` variable in `mining_calc.py`. Common alternatives:
- **Python**: 224t cargo, 3 lasers, 3 controllers
- **Type-9 Heavy**: 512t cargo, 3 lasers, 4 controllers
- **Imperial Cutter**: 512t cargo, 4 lasers, 5 controllers

---

## 🛠️ Technical Details

### Data Sources

| Source | Purpose | Update Frequency |
|--------|---------|------------------|
| [EDTools.cc](https://edtools.cc/miner) | Hotspots, buyer prices | Community-driven |
| [EDSM API](https://www.edsm.net/) | System coordinates | Real-time |

### Caching

- **Coordinates**: 10 minutes (systems don't move)
- **Buyer data**: 2 minutes (prices change frequently)
- **Hotspots**: 5 minutes (locations are stable)

### Error Handling

- **Exponential backoff**: 3 retry attempts with increasing delays
- **Fallback logic**: Continues processing other commodities on failure
- **Data validation**: Filters stale data (>12 hours old)

---

## 🤝 Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Ideas for Features

- 🔧 Browser automation fallback (when API is down)
- 📊 Notion integration (track mining sessions)
- 🚀 Ship comparison tool
- 💎 Core mining support
- 🎯 Overlap hotspot detection
- 🛰️ Fleet carrier integration

---

## 📜 License

MIT License - see [LICENSE](LICENSE) for details

---

## 🙏 Credits

- **Data Sources**: [EDTools.cc](https://edtools.cc/), [EDSM](https://www.edsm.net/)
- **Community**: Elite Dangerous mining subreddit & Discord
- **Inspiration**: Real CMDR feedback on realistic time calculations

---

## 📞 Support

- 🐛 **Bug Reports**: [Open an issue](https://github.com/vivladius/elite-mining-calculator/issues)
- 💡 **Feature Requests**: [Open an issue](https://github.com/vivladius/elite-mining-calculator/issues)

---

**Fly safe, CMDR o7**
