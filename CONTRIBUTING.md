# Contributing to Elite Dangerous Mining Calculator

Thank you for your interest in contributing! This document provides guidelines for contributing to the project.

---

## 🚀 Quick Start for Contributors

### 1. Fork & Clone

```bash
# Fork the repository on GitHub (click "Fork" button)

# Clone your fork
git clone https://github.com/YOUR_USERNAME/elite-mining-calculator.git
cd elite-mining-calculator

# Add upstream remote
git remote add upstream https://github.com/vivladius/elite-mining-calculator.git
```

### 2. Create a Branch

```bash
# Create a new branch for your feature
git checkout -b feature/your-feature-name

# Or for bug fixes
git checkout -b fix/bug-description
```

### 3. Make Changes

- Write clean, readable code
- Follow existing code style
- Add comments for complex logic
- Update documentation if needed

### 4. Test Your Changes

```bash
# Run the calculator
python mining_calc.py

# Test with different systems
# Test with different mining modes
# Verify calculations are correct
```

### 5. Commit & Push

```bash
# Stage your changes
git add .

# Commit with a clear message
git commit -m "Add feature: ship comparison tool"

# Push to your fork
git push origin feature/your-feature-name
```

### 6. Create Pull Request

1. Go to your fork on GitHub
2. Click "Pull Request" button
3. Describe your changes clearly
4. Wait for review

---

## 📝 Contribution Guidelines

### Code Style

- **Python 3.8+** syntax
- **PEP 8** formatting (mostly)
- **Type hints** for function signatures
- **Docstrings** for public functions
- **Comments** for non-obvious logic

### Good Commit Messages

✅ **Good:**
```
Add Type-9 Heavy ship profile with 512t cargo
Fix bulk tax calculation for zero demand stations
Update README with installation instructions
```

❌ **Bad:**
```
fixed stuff
update
changes
```

### Pull Request Checklist

- [ ] Code runs without errors
- [ ] No breaking changes to existing features
- [ ] Documentation updated (if needed)
- [ ] Clear description of changes
- [ ] Tested manually

---

## 🎯 Areas for Contribution

### High Priority

1. **Additional Ship Profiles**
   - Python, Type-9, Cutter, Anaconda, etc.
   - Include realistic cargo/jump/laser specs

2. **Core Mining Support**
   - Seismic charge mechanics
   - Subsurface deposit calculations
   - High-value commodities (Rhodplumsite, Alexandrite)

3. **Browser Automation Fallback**
   - Scrape EDTools.cc when API fails
   - Maintain 99% uptime

4. **Unit Tests**
   - Test `evaluate_route()` calculations
   - Test bulk tax logic
   - Test travel time calculations

### Medium Priority

5. **Overlap Hotspot Detection**
   - Flag overlapping hotspots (30-50% yield bonus)
   - Prioritize overlap routes

6. **Fleet Carrier Integration**
   - Find nearby carriers buying commodities
   - Compare carrier vs station prices

7. **Ship Comparison Tool**
   - Compare multiple ships side-by-side
   - Show trade-offs (cargo vs jump range)

8. **Notion Integration**
   - Track mining session history
   - Calculate prediction accuracy

---

## 🐛 Bug Reports

When reporting bugs, include:

1. **Python version**: `python --version`
2. **Operating system**: Windows/Mac/Linux
3. **Error message**: Full traceback
4. **Steps to reproduce**: What you did
5. **Expected vs actual**: What should happen vs what happened

---

## 💡 Feature Requests

When requesting features, include:

1. **Use case**: Why is this needed?
2. **Expected behavior**: What should it do?
3. **Example**: Show how it would work
4. **Priority**: How important is this?

---

## 🙏 Thank You!

Every contribution helps make this tool better for the Elite Dangerous mining community.

**Fly safe, CMDR o7**
