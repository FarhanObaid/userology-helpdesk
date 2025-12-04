# How I Rebuilt the Userology Help Center: A Product Thinking Journey

**Author:** Farhan Obaid  
**Last Updated:** December 1, 2025

---

## The Story in 30 Seconds

I started with zero web development experience and a broken help center. I ended up shipping a modern, searchable, user-friendly knowledge base. This document isn't about the code—it's about **how I thought through the problem**, made decisions under uncertainty, and learned to blend human judgment with AI-assisted execution.

If you're evaluating my product thinking, this is where you'll see it.

---

## Table of Contents

1. [Where I Started (And Why That Mattered)](#1-where-i-started-and-why-that-mattered)
2. [The First Thing I Did: Become a User](#2-the-first-thing-i-did-become-a-user)
3. [What I Found: The Four Broken Pillars](#3-what-i-found-the-four-broken-pillars)
4. [How I Chose What to Fix First](#4-how-i-chose-what-to-fix-first)
5. [My Tool Journey: What Worked, What Failed, What I Learned](#5-my-tool-journey-what-worked-what-failed-what-i-learned)
6. [The Rebuild: What I Built and Why](#6-the-rebuild-what-i-built-and-why)
7. [The Decisions That Shaped Everything](#7-the-decisions-that-shaped-everything)
8. [What Didn't Work (And What I Learned From It)](#8-what-didnt-work-and-what-i-learned-from-it)
9. [How I'd Measure Success](#9-how-id-measure-success)
10. [What This Taught Me About Product Thinking](#10-what-this-taught-me-about-product-thinking)

---

## 1. Where I Started (And Why That Mattered)

I want to be upfront: **I had no prior experience building or redesigning websites.**

That sounds like a disadvantage. It wasn't.

Here's why: When you don't have technical baggage, you can't hide behind "that's how it's always done." You're forced to think like a user, question everything, and make decisions based on *what should happen* rather than *what's easy to implement*.

My first steps were deliberately simple:
1. I forked the repository and opened it in VS Code
2. I ran the site locally using Live Server
3. I opened it in my browser and pretended I was a confused Userology user looking for help

That last step was the most important. I wasn't auditing code—I was auditing an *experience*.

---

## 2. The First Thing I Did: Become a User

Before touching any code, I spent time living inside the help center as a user would. I asked myself simple questions:

- *"I just signed up for Userology. Where do I start?"*
- *"I want to set up my first study. Can I find that information quickly?"*
- *"I have a specific question about AI transcripts. Can I search for it?"*
- *"I prefer video tutorials. Are they easy to find?"*

The answers were... not great.

I documented every moment of friction. Every time I felt lost, confused, or frustrated, I wrote it down. This wasn't a formal usability test—it was just me, a notepad, and honest reactions.

**Why this mattered:** Many redesigns start with "what looks outdated?" I started with "what feels broken?" That distinction shaped every decision that followed.

---

## 3. What I Found: The Four Broken Pillars

After my user walkthrough, I grouped problems into four pillars that define documentation UX. This framework helped me think systematically rather than randomly fixing things.

### Pillar 1: Search — "I know what I want, but I can't find it"

**The Problem:** There was a beautiful search bar in the hero section. It looked great. It did absolutely nothing.

**Why This Hurt:** Help centers live or die by search. [Research shows](https://www.nngroup.com/articles/search-visible-and-simple/) that 50%+ of help center users go straight to search. A non-functional search bar is worse than no search bar—it actively misleads users.

**The User Feeling:** *"I typed my question. Nothing happened. Is this site broken? Should I just email support?"*

### Pillar 2: Discovery — "I don't know what I'm looking for, help me explore"

**The Problem:** The All Articles page was a flat list of 24 links. The Videos page was a basic grid of 27 thumbnails. No categories. No filters. No way to browse by topic.

**Why This Hurt:** Users who don't have a specific question need to browse. A flat list forces them to read every title sequentially. That's exhausting.

**The User Feeling:** *"There's so much content here, but I can't tell what's relevant to me."*

### Pillar 3: Comprehension — "I found the article, but it's hard to read"

**The Problem:** Articles had inconsistent typography, cramped spacing, and redundant elements (duplicate "Related Articles" sections, unnecessary TOC widgets).

**Why This Hurt:** Even if users find the right article, poor readability means they won't finish it—or won't absorb the information.

**The User Feeling:** *"This article probably has my answer, but it's overwhelming to look at."*

### Pillar 4: Navigation — "I'm in the middle of the site. Now I'm lost."

**The Problem:** Breadcrumbs were inconsistent. There was no clear "escape hatch" when users couldn't find what they needed. The sidebar navigation existed but felt disconnected.

**Why This Hurt:** Users need to know where they are, where they can go, and what to do if they're stuck.

**The User Feeling:** *"I've been clicking around for five minutes. I don't know how to get back. I'm just going to email support."*

---

## 4. How I Chose What to Fix First

Here's where product thinking really matters. I had limited time and dozens of problems. I couldn't fix everything. So I created a simple prioritization framework:

### My Three Rules

**Rule 1: Impact Over Effort**
Fix things that dramatically improve user experience, even if they're harder. A working search bar affects every single user. Slightly better fonts affect... no one urgently.

**Rule 2: Foundations Before Polish**
Get the structure right before adding animations. Establish a design system before tweaking colors. Make it *work* before making it *pretty*.

**Rule 3: Entry Points and Exit Points First**
Users enter through the homepage hero and search. They exit through "Related Articles" or a support CTA. Fix those first—they define the entire journey.

### The Sequence That Emerged

Based on these rules, I prioritized in this order:

```
1. Design system (consistent foundation)
2. Global search (primary user need)
3. Article layout cleanup (remove noise, improve readability)
4. All Articles page redesign (enable discovery)
5. Videos page redesign (match articles, enable discovery)
6. Homepage polish (popular articles, support CTA)
7. Micro-interactions (hover states, cards, responsive refinements)
```

**Why this order?** Each step built on the previous one. I couldn't redesign article cards until I had a design system. I couldn't improve discovery until individual articles were clean. The sequence wasn't arbitrary—it was structural.

---

## 5. My Tool Journey: What Worked, What Failed, What I Learned

I experimented with several AI tools during this project. Here's an honest breakdown of what happened.

### Tool 1: Antigravity — The Overconfident Assistant

**Why I tried it:** I wanted a fast AI audit and automated fixes. The promise was appealing—let AI analyze the codebase and suggest improvements.

**What happened:** It produced generic recommendations and attempted bulk changes. Several of these broke article pages. It would confidently make edits without understanding the repo structure or the relationships between files.

**Why it failed:** Antigravity tried to be *prescriptive* without being *contextual*. It treated the helpdesk like a generic website rather than understanding the specific content structure (24 articles, 27 videos, 7 section pages, etc.).

**Lesson learned:** AI tools that try to "do it all" often do nothing well. I needed tools that were good at specific tasks, not tools that promised to handle everything.

### Tool 2: Augment Code — The Reliable Executor

**Why I tried it:** After Antigravity's failures, I needed a tool for controlled, large-scale code refactors that wouldn't break things.

**What it did well:**
- Made consistent design-system changes across 30+ files
- Implemented complex JavaScript (search logic, filter/sort functionality)
- Handled large file updates without losing context
- Preserved existing content while restructuring layouts

**Why it worked:** Augment Code didn't try to make decisions for me. It executed what I asked for, accurately and at scale. I was the product thinker; it was the implementation engine.

### Tool 3: Google Stitch AI — The Design Partner

**Why I tried it:** For focused UI/UX suggestions, especially when I wasn't sure how to visually structure the All Articles and Videos pages.

**What it did well:**
- Suggested card-based layouts with proper hierarchy
- Recommended responsive grid approaches
- Proposed micro-interactions (hover effects, play overlays)
- Helped me think through component structure

**Why it worked:** Stitch AI was narrow and focused. It didn't try to write my code—it helped me think through design decisions, which I then implemented with Augment Code.

### The Winning Combination

```
Stitch AI → Design thinking and component ideas
Augment Code → Accurate, large-scale implementation
Me → Problem identification, prioritization, and final decisions
```

**The meta-lesson:** AI tools work best when they have clear, limited roles. The moment I tried to use one tool for everything, quality dropped. The moment I assigned specific jobs to specific tools, productivity soared.

---

## 6. The Rebuild: What I Built and Why

Here's everything I shipped, organized by the problem it solved.

### Solving Search: Global Search Implementation

**What I built:**
- Real-time dropdown search that shows matching articles as you type
- Keyboard navigation (arrow keys to move, Enter to select, Escape to close)
- Highlighted matching text so users see why results matched
- Pre-built article index for instant search performance

**Why this design:**
I studied how Intercom, Zendesk, and Algolia handle help center search. The pattern is consistent: show results *inline* as users type. Don't make them press Enter and wait for a new page. Instant feedback reduces friction and helps users refine their queries.

### Solving Discovery: All Articles & Videos Page Redesign

**What I built:**
- Search bar at the top of each page for filtering
- Category filter tabs (8 categories for articles, 8 for videos)
- Sort dropdown (A-Z, Z-A, by Category)
- 3-column responsive card grid with enhanced visual design
- Dynamic count display ("Showing 12 videos")
- "No results found" state with support CTA fallback

**Why this design:**
I benchmarked against Stripe Docs, Notion Help, and Linear Docs. The pattern is clear: **filter → sort → scan → click**. Users want to narrow down options quickly, then visually scan what's left. A flat list forces sequential reading. A filtered grid enables parallel scanning.

The category tabs came from analyzing the existing content. I grouped articles and videos by topic (Study Setup, Interview Plan, Responses, Results, etc.) so users could self-select their area of interest.

### Solving Comprehension: Article Cleanup

**What I built:**
- Removed duplicate "Related Articles" sections (kept only the clean 3-column grid at the bottom)
- Removed redundant "On this page" TOC widgets
- Established consistent typography and spacing using CSS custom properties

**Why this design:**
I followed the principle of *progressive disclosure*: show only what users need at each moment. Two related article sections confused users about which to click. A TOC that duplicated the sidebar navigation added noise without value.

Less clutter = better comprehension.

### Solving Navigation: Support CTAs and Escape Hatches

**What I built:**
- "Still looking for an answer?" cards on Browse Topics, All Articles, and Videos pages
- Consistent placement at the bottom of content pages
- Clear call-to-action: "Contact Support" linking to support@userology.co.in

**Why this design:**
Every page needs an "escape hatch." If users can't find what they need through self-service, they should know exactly what to do next. Hiding the support option makes users feel trapped. Surfacing it builds trust.

I placed the CTA at the bottom of each page because that's where users end up after scanning all content. If they've scrolled to the bottom and still haven't found their answer, the CTA appears right where they need it.

### Solving First Impressions: Popular Articles Enhancement

**What I built:**
- Redesigned homepage section with 6 featured articles
- Card-based layout with category tags, titles, descriptions
- "View All Articles" button for deeper exploration
- Consistent styling with hover effects

**Why this design:**
First-time users don't know what they're looking for. Surfacing popular content gives them starting points. The card design makes each article scannable—users can quickly assess relevance without clicking.

---

## 7. The Decisions That Shaped Everything

Beyond individual features, there were a few meta-decisions that influenced the entire project.

### Decision 1: Benchmark Obsessively

Before building anything, I spent hours in other help centers:
- **Maze** — for design system inspiration (colors, typography, spacing)
- **Linear** — for layout patterns (sidebar navigation, article structure)
- **Dovetail** — for information architecture (how they organize topics)
- **Intercom & Zendesk** — for search and discovery patterns

**Why this mattered:** I wasn't inventing patterns. I was *borrowing* proven patterns from products with dedicated UX teams and years of iteration. This reduced risk and accelerated decisions.

### Decision 2: Design System First

Before fixing any single page, I established:
- Color tokens (`--u-color-primary: #0057FF`)
- Spacing scale (`--u-space-1` through `--u-space-16`)
- Border radius standards (`--u-radius-sm`, `-md`, `-lg`)
- Shadow definitions (`--u-shadow-sm`, `-md`, `-lg`)
- Typography with Inter font

**Why this mattered:** A design system is an investment that pays dividends. Every subsequent change was faster because I wasn't making decisions about colors or spacing—I was using pre-defined tokens.

### Decision 3: Consistency Over Creativity

I deliberately made the Videos page look almost identical to the Articles page. Same toolbar structure. Same filter tabs. Same card grid. Same support CTA.

Some might call this boring. I call it *learnable*.

**Why this mattered:** When users learn one pattern, they can apply it everywhere. A unique design for each page forces users to relearn navigation. Consistency reduces cognitive load.

### Decision 4: Responsive from the Start

Every component was designed with three breakpoints in mind:
- Desktop (1200px+): 3-column grids
- Tablet (768-1024px): 2-column grids
- Mobile (<768px): Single column, stacked layout

**Why this mattered:** Mobile isn't an afterthought—it's often the primary experience. Retrofitting responsiveness is painful. Building it from the start is just... building.

---

## 8. What Didn't Work (And What I Learned From It)

Honest reflection matters. Here's where I stumbled.

### Failure 1: Trusting AI Too Early

**What happened:** In my excitement to move fast, I let Antigravity make sweeping changes across multiple files. Several article pages broke. Content was mangled. I had to revert and start over.

**What I learned:** AI tools are powerful accelerators, but they need human oversight. The time I "saved" by letting AI run unsupervised was lost (and then some) in debugging.

**New rule:** Always review AI-generated changes in a local environment before committing. No exceptions.

### Failure 2: Underestimating Edge Cases

**What happened:** My first search implementation worked great for simple queries. But it broke when users typed special characters, or when articles had unusual titles.

**What I learned:** Happy-path testing isn't enough. I should have tested with weird inputs, empty states, and boundary conditions from the start.

**New rule:** Test the edges before celebrating the center.

### Failure 3: Trying to Do Too Much at Once

**What happened:** At one point, I tried to redesign the article layout, add the feedback widget, AND improve the sidebar navigation all in one session. I got confused. Changes conflicted. I made more mistakes.

**What I learned:** Small, focused changes are safer than big, ambitious ones. Commit frequently. Celebrate small wins.

**New rule:** One problem at a time. Ship it. Then move to the next.

---

## 9. How I'd Measure Success

If this were a real product launch, here's how I'd know if it worked:

### Primary Metrics

| Metric | What It Measures | Target |
|--------|------------------|--------|
| **Search usage rate** | % of sessions that use search | >40% |
| **Search success rate** | % of searches that lead to an article click | >60% |
| **Time to first article** | How long until users reach content | <30 seconds |
| **Support ticket volume** | Contacts for questions answered in docs | ↓20% |

### Secondary Metrics

| Metric | What It Measures | Why It Matters |
|--------|------------------|----------------|
| **Pages per session** | How much users explore | Higher = better discovery |
| **Bounce rate** | Users who leave immediately | Lower = content matches expectations |
| **Helpfulness votes** | "Was this helpful?" responses | Signals content quality |
| **Filter/sort usage** | How often filtering is used | Validates feature value |

### Qualitative Signals

- User feedback: "I found what I needed quickly"
- Support team feedback: "Fewer 'how do I...' questions"
- Return visits: Users coming back to find more content

---

## 10. What This Taught Me About Product Thinking

This project crystallized a few beliefs about how to build good products.

### Belief 1: Start With Problems, Not Solutions

It's tempting to start with "let's add a cool search feature." That's solution-first thinking.

Better: "Users can't find content. What's the fastest path to an answer?" That's problem-first thinking.

The difference is subtle but crucial. Solution-first thinking leads to features nobody needs. Problem-first thinking leads to features that matter.

### Belief 2: Constraints Are Gifts

I had no web development experience. I had limited time. I had a messy codebase.

These constraints forced clarity:
- No experience → Think like a user, not a developer
- Limited time → Prioritize ruthlessly
- Messy codebase → Clean up foundations before adding features

Without constraints, I might have over-engineered. With constraints, I built what was necessary.

### Belief 3: AI Amplifies, It Doesn't Replace

AI tools made me 10x faster at *execution*. They didn't help with *decisions*.

The hardest parts of this project—figuring out what to build, in what order, and why—were entirely human. AI helped me implement those decisions faster. That's the right relationship.

### Belief 4: Consistency Compounds

Every time I made a consistent decision (same card style, same spacing, same hover effect), future decisions got easier. The design system paid dividends immediately.

Inconsistency is debt. Consistency is investment.

### Belief 5: Done Is Better Than Perfect

I shipped a help center that's dramatically better than what existed before. It's not perfect. The search could be smarter. The filtering could be more sophisticated. The mobile experience could be smoother.

But it's *live*. It's *working*. It's *helping users*.

Perfect is the enemy of shipped. I chose shipped.

---

## Final Reflection

I started this project without knowing how to build a website. I ended it with a shipped product and a clearer understanding of what product thinking actually means.

Product thinking isn't about having all the answers. It's about:
- Asking the right questions ("What's broken for users?")
- Making principled tradeoffs ("Impact over effort")
- Using tools appropriately ("AI for execution, humans for decisions")
- Shipping and iterating ("Done is better than perfect")

This help center isn't the end of a project. It's the beginning of a product that can now improve based on real user feedback.

And that's exactly how it should be.

---

## Appendix: Quick Reference

### Files I Modified

| Category | Count | Files |
|----------|-------|-------|
| Core pages | 4 | `index.html`, `categories.html`, `articles.html`, `videos.html` |
| Article pages | 24 | All `article_*.html` files |
| Section pages | 7 | All `section_*.html` files |
| Styles | 1 | `css/style.css` (~500 lines added) |
| JavaScript | 1 | `js/main.js` (~250 lines added) |

### Key Features Shipped

1. ✅ Functional global search with keyboard navigation
2. ✅ All Articles page with search, filter, and sort
3. ✅ Videos page with search, filter, and sort
4. ✅ Enhanced card layouts with hover effects
5. ✅ Support CTA cards on discovery pages
6. ✅ Popular Articles section on homepage
7. ✅ Cleaned up article pages (removed duplicates, TOC)
8. ✅ Consistent design system across all pages
9. ✅ Responsive design for all breakpoints

### Tools Used

| Tool | Role | Verdict |
|------|------|---------|
| Antigravity | General AI audit | ❌ Failed — too blunt, caused breakages |
| Augment Code | Code implementation | ✅ Worked — accurate, reliable, scalable |
| Google Stitch AI | Design suggestions | ✅ Worked — focused, helpful for UI decisions |
| VS Code + Live Server | Development environment | ✅ Essential — local testing prevented disasters |

---

*If you've read this far, thank you. I hope this document gave you insight into how I think about building products. I'd welcome any feedback or questions.*

