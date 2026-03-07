# Ruby GSoC 2026 Proposal (Final Draft)

## Project Selection
- **Organization:** Ruby
- **Proposed Project:** RubyGems.org — Ruby Vulnerability Warnings
- **Project Size:** Medium (175h)
- **Domain:** Security
- **Mentors (from ideas list):** @colby-swandale, @jenshenny

---

## Student/Contributor Application (All 16 Questions)

### 1) Contact information
- **Name:** [Your Full Name]
- **Email:** [your.email@example.com]
- **GitHub:** [your-github-username]
- **Location:** [City, Country, Timezone]

### 2) What project do you want to work on?
I want to work on **RubyGems.org — Ruby Vulnerability Warnings** from the Ruby GSoC 2026 ideas list. The project goal is to surface vulnerability warnings directly on gem pages so users can quickly identify known vulnerabilities and make safer dependency decisions.

### 3) Why Ruby and why Ruby GSoC?
I like Ruby because of its developer-first design, strong ecosystem, and readable code that encourages maintainability. I want to contribute through Ruby GSoC because it combines real community impact with mentorship, and this project directly improves supply-chain security for the global Ruby community.

### 4) Experience with Ruby, C, and other languages
- **Ruby:** [Describe your current level: beginner/intermediate/advanced + projects]
- **Rails:** [Any CRUD/API/background-jobs experience]
- **C:** [No experience / basic / moderate]
- **Other languages:** [Python/JavaScript/Java/etc + what you used them for]
- **Testing:** [RSpec/Minitest/CI experience]

### 5) Educational background
I am currently [degree/program] at [institution], focused on [major/specialization]. Relevant coursework includes [data structures, DBMS, security, web engineering, etc.].

### 6) Past pull requests to Ruby OSS projects
- [PR Link 1]
- [PR Link 2]
- [Issue/Discussion Link if available]

If accepted, I will continue submitting small PRs before coding starts (docs/tests/bug fixes) to improve codebase familiarity and communication with maintainers.

### 7) Other commitments during GSoC
My primary commitment during GSoC is this project. I have [briefly mention exams/internship/family commitments if any], and I have planned my schedule to consistently contribute **~35–40 hours/week** during coding periods.

### 8) Planned vacations/trips
I have [no major travel planned / one short trip from date to date]. If any unavoidable travel occurs, I will communicate it in advance and adjust milestones to avoid delivery risk.

### 9) Summer classes
I am taking [number] class(es): [course names]. I have verified that class workload will not conflict with the coding schedule.

### 10) Other employment
I have [no other employment / part-time role of X hours]. My project schedule is designed to maintain required weekly contribution and mentor communication cadence.

### 11) Previous GSoC participation
I have [not] participated in GSoC before.
If yes: [org/project/year + mentor contact].

### 12) Detailed project proposal

#### Problem statement
Ruby users currently lack a clear, official warning signal on RubyGems.org when a gem has known vulnerabilities. This creates risk in dependency selection and delays remediation.

#### Objective
Build a robust warning system in RubyGems.org that identifies vulnerable gems and displays clear warnings to users on relevant gem pages.

#### Scope
1. Design a vulnerability data ingestion layer that can consume advisory metadata from supported sources.
2. Normalize advisory data into a consistent internal model.
3. Match advisories to gem name and affected version ranges.
4. Display warning banners/messages on gem pages and version pages.
5. Add tests, admin/ops visibility, and documentation.

#### Technical approach
- **Backend:** Ruby on Rails service objects for advisory ingestion and matching.
- **Data model:** tables for advisory source, package name, affected ranges, severity, references, and update timestamps.
- **Matching logic:** semantic version range checks against gem versions.
- **UI:** non-intrusive warning component with severity + advisory links.
- **Updates:** scheduled refresh job with safe retry and observability logs.
- **Policy note:** respect licensing boundaries; avoid directly embedding GPL-only implementation code.

#### Deliverables
- Advisory ingestion + normalization pipeline.
- Vulnerability-to-gem matching engine.
- User-facing warning UI on affected gems/versions.
- Full automated test coverage for key paths.
- Documentation for maintainers and future contributors.

### 13) Timeline and milestones

#### Community Bonding (before coding)
- Finalize requirements with mentors and confirm advisory-source strategy.
- Set up local RubyGems.org dev environment and run baseline tests.
- Submit at least one warm-up PR (docs/test cleanup or small bug fix).

#### Coding Phase 1 (Weeks 1–3)
- Implement DB schema/migrations for advisory entities.
- Add import pipeline skeleton + source adapter interface.
- Seed with controlled sample advisories for deterministic tests.
- **Milestone:** advisories stored and queryable in development.

#### Coding Phase 2 (Weeks 4–6)
- Implement gem/version range matcher.
- Build service layer for “is this gem version vulnerable?” checks.
- Add unit tests for version-range edge cases.
- **Milestone:** reliable matching engine with high test confidence.

#### Midterm checkpoint (end of Week 6)
- Demo end-to-end advisory ingestion + matching on sample gems.
- Mentor feedback incorporated into scope refinements.

#### Coding Phase 3 (Weeks 7–9)
- Integrate warning UI on gem and version pages.
- Add severity labels + external advisory reference links.
- Improve performance for gem page rendering paths.
- **Milestone:** feature visible to end users behind configurable flag.

#### Coding Phase 4 (Weeks 10–12)
- Scheduled refresh job + error handling + monitoring logs.
- Integration tests, regression tests, and docs.
- Final hardening, code cleanup, and PR polishing.
- **Final milestone:** production-ready vulnerability warning feature with docs.

#### Buffer (last days)
- Address mentor review comments.
- Add stretch improvements if core scope is complete.

### 14) Hobbies and personal background
Outside coding, I enjoy [hobby 1], [hobby 2], and [hobby 3]. These activities help me stay disciplined and creative. Long-term, I want to build reliable developer tools and security-focused open source software.

### 15) A question I propose + answer
**Q:** How will you ensure this project remains maintainable after GSoC?

**A:** I will keep architecture modular (separate ingestion, matching, and UI layers), write clear contributor docs, provide robust test coverage, and keep PRs small and reviewable. This reduces onboarding friction for future maintainers.

### 16) Bonus: Inclusion in open source
To improve participation from women and underrepresented groups, projects should combine mentorship, psychologically safe communication norms, beginner-friendly issue labels, and transparent contribution pathways. Concrete actions include office hours, public onboarding docs, and active recognition of new contributors.

---

## Risk Management
- **Risk:** Advisory data inconsistency across sources  
  **Mitigation:** Normalization layer + strict schema validation + fallback parsing.

- **Risk:** Incorrect version matching  
  **Mitigation:** Extensive tests for edge cases and real-world sample advisories.

- **Risk:** Performance impact on gem pages  
  **Mitigation:** Query optimization, caching strategy, and benchmark checks.

- **Risk:** Scope overflow  
  **Mitigation:** Prioritize MVP (accurate warning signal) before advanced features.

---

## Communication Plan
- Daily async updates in mentor channel.
- Weekly progress summary with blockers, completed tasks, and next milestones.
- Immediate escalation when blocked >24 hours.
- PR-first workflow with frequent, small, reviewable changes.

---

## Pre-Submission Checklist
- [ ] Replace all bracket placeholders with your details.
- [ ] Add actual PR/issue/discussion links.
- [ ] Confirm timezone and weekly availability.
- [ ] Share draft with mentors on Slack/Discord before final submission.
- [ ] Paste final content into the GSoC web application.
