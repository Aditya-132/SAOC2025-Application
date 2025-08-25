# SAoC 2025 Project Proposal: D Compiler Performance Regression Publisher

**SAoC 2025 Project Proposal: D Compiler Performance Regression Publisher**

**Applicant:** Aditya Chincholkar  
**GitHub:** [https://github.com/Aditya-132](https://github.com/Aditya-132)  
**Expected Mentor:** Dennis Korpel  
**Project Duration:** 4 months (September - December 2025, completing January 14, 2026)  
**Weekly Commitment:** 20 hours/week  

---

## My Previous Experience with D

I have solid experience contributing to the D ecosystem, particularly with performance optimizations in Phobos. My merged contributions include:

### Phobos Contributions
- **Adding lazycache function in std.algorithm.iteration** [#10687](https://github.com/dlang/phobos/pull/10687) – Added new caching functionality to improve algorithm performance  
- **Optimizing powmod function for ulong** [#10513](https://github.com/dlang/phobos/pull/10513) – Performance improvements for modular exponentiation  
- **Optimizing and fixing bug in Complex!float.abs/hypot** [#10491](https://github.com/dlang/phobos/pull/10491) – Fixed correctness issues while improving performance  
- **Optimization of std.conv.parse!(int, string)** [#9829](https://github.com/dlang/phobos/pull/9829) – String parsing performance improvements  
- **Fixing error in cbrt function** [#10577](https://github.com/dlang/phobos/pull/10577) – Correctness fix for cube root calculations  

This experience has given me deep familiarity with D's standard library, performance optimization techniques, and the contribution process. More importantly, it's shown me firsthand how performance claims in PRs need proper verification – which is exactly what this project addresses.  

---

## Project Description

This project is about building an automated performance monitoring system for the **DMD compiler**.  

Currently, when people submit pull requests claiming compiler performance improvements, there’s no reliable way to verify those claims. Reviewers must either trust the contributor, manually benchmark, or skip performance validation altogether.  

I want to build a system that **automatically checks compiler performance for every pull request**, tracking metrics such as:  

- Compiled binary size (e.g., "hello world")  
- Compilation time for real D projects  
- DMD executable size growth  
- Test suite runtime  
- Memory usage during compilation  

The plan includes:  

- A bot that automatically comments on PRs with performance results  
- A website for historical performance data visualization  
- Stress tests to detect performance regressions  

**Goal:** Make compiler performance visible and measurable, enabling better review decisions and early regression detection.  

---

## Why D Needs This Project

Current issues with DMD performance reviews:  

1. Reviewers must **trust contributors’ claims**.  
2. Reviewers must **manually test performance**, which is time-consuming.  
3. Performance checks are often **skipped entirely**.  

Problems caused:  
- Inconsistent verification of performance claims  
- Small slowdowns accumulate unnoticed  
- Manual benchmarking is wasted effort  
- No community-wide performance history exists  

D’s features (templates, CTFE, mixins) introduce unpredictable performance impacts. For example, D projects like **vibe.d** and **mir** may compile slower after an update, but there’s no way to track what caused the slowdown.  

This project solves these issues by **adding automated PR performance checks** and maintaining a **historical performance database**.  

---

## What I've Built (Foundation in Place)

Even though this project wasn’t selected for **GSoC 2025**, I continued working independently.  

### Current Implementation

**GitHub Actions Integration**  
- Workflow triggers on PR submissions  
- Automated performance data collection  
- Statistical analysis (multiple runs to reduce variance)  
- Automatic PR comments with performance results  
- Error handling and logging for reliability  

**Performance Testing Framework**  
- Compilation timing tests (templates, CTFE, simple builds)  
- Memory usage tracking  
- Cross-platform execution (Linux GitHub Actions runners)  
- JSON output format for dashboard integration  

**Working Demonstrations**  
- [Live GitHub Actions Demo](https://github.com/Aditya-132/dmd/actions/runs/16852532295/job/47740888538?pr=3)  
- [PR Integration Example](https://github.com/Aditya-132/dmd/pull/3)  
- [Development Branch](https://github.com/Aditya-132/dmd/tree/PRT)  

---

## 4-Month Development Plan

### Milestone 1 (September 2025): Enhanced Results Publishing System
- Expand performance metrics collection  
- Add binary size, compiler size, test runtime, memory usage  
- Support multiple compiler configurations (debug, release, cross-platform)  
- Standardize JSON output format  
- Integrate PR status checks to block regressions  

**Deliverable:** Production-ready GitHub Actions bot.  

---

### Milestone 2 (October 2025): Comprehensive Stress Testing Suite
- **Template stress tests** (deep recursion, large instantiations)  
- **CTFE stress tests** (memory-intensive operations, recursive calls)  
- **Real-world benchmarks** (vibe.d, mir, dub)  
- Incremental compilation scenarios  

**Deliverable:** Expanded stress test suite.  

---

### Milestone 3 (November 2025): Web Dashboard Development
- **Backend:** vibe.d with RESTful API  
- **Database:** PostgreSQL for time-series data  
- **Frontend:** Visualization with trend charts, regression detection  
- GitHub OAuth for access control  

**Deliverable:** Fully functional web dashboard.  

---

### Milestone 4 (December 2025 – January 2026): Production Deployment
- Deploy hosting & infrastructure  
- Monitoring, alerting, backup systems  
- Optimize database performance  
- Documentation for contributors  
- Official **dlang/dmd repository integration**  

**Deliverable:** Production-ready system integrated into D’s infrastructure.  

---

## Technical Implementation

**Current Architecture**  

- **Performance Metrics Collection:** Compilation time, test suite runtime, binary size, memory usage  
- **GitHub Actions:** Data collection → JSON artifacts  
- **PostgreSQL Database:** Historical data storage  
- **vibe.d Backend:** Data processing via RESTful API  
- **Web Dashboard:** Visualization & regression alerts  

---

## Web Dashboard Features
- Time-series visualization of performance evolution  
- Automated regression detection  
- Historical compiler version comparison  
- Community-accessible transparency  

**Why vibe.d?**  
- Native D performance  
- Easy for DMD contributors to maintain  
- Full-stack D ecosystem demonstration  

---

## Expected Outcomes

By **December 2025**:  
- Automated PR performance verification  
- Comprehensive stress testing suite  
- Historical performance database with ≥4 months of data  
- Production web dashboard serving the D community  
- Official repository integration  

---

## Success Metrics
- 100% DMD PR coverage with automated analysis  
- Sub-5-minute feedback delivery  
- 20+ new stress tests  
- Active dashboard usage  
- Early regression detection  

---

## My Commitment

I will contribute **20 hours/week for 4 months**, delivering:  
- Production-ready testing system  
- Comprehensive documentation  
- Regular progress updates  
- Official integration with D repos  

---

## Current Implementation Links

- [Forum Discussion](https://forum.dlang.org/post/gxlnfhkewtcdvsqkxtwr@forum.dlang.org)  
- [GitHub Actions Demo](https://github.com/Aditya-132/dmd/actions/runs/16852532295/job/47740888538?pr=3)  
- [Test PR Example](https://github.com/Aditya-132/dmd/pull/3)  
- [Development Branch](https://github.com/Aditya-132/dmd/tree/PRT)  
