# Audit & Testing Documentation: I used Google Lighthouse that is integraded in chrome

This document records performance, accessibility, SEO, and quality audit benchmarks conducted using Google Lighthouse during the manual testing phase of development of Kwena Ka Bobedi Website

## 1. Audit Standards & Targets

To maintain quality across releases, target scores for production builds are:

| Metric Category | Target Score | Minimum Acceptable |

| **Performance** | ≥ 90 | 43 |
| **Accessibility** | 100 | 76 |
| **Best Practices** | 100 | 96 |
| **SEO** | 100 | 90 |
| **PWA** | Pass core checks | Pass core checks |

## 2. Test Environment & Setup

**Browser:** Google Chrome (Incognito / My Profile)
**Testing Tool:** Chrome DevTools / Lighthouse CLI and Speedpage
**Throttling:** Applied (Simulated Moto G4 / Slow 4G for mobile test runs)
**Extensions:** Disabled (to prevent artificial performance degradation)

## 3. Lighthouse Audit History Log

### 📅 Date: [2026-10-16]
**Branch / Commit:** `main` @ `[commit-hash]`
Environment:
**Tester:** [Simphiwe Dladla / Project Manager and QA Tester]

## 4. Identified Issues & Action Items

| Issue Description , Category , Impact , Status / Ticket 

Requests are blocking the page's initial render, which may delay LCP. Deferring or inlining can move these network requests out of the critical path.

A forced reflow occurs when JavaScript queries geometric properties (such as offsetWidth) after styles have been invalidated by a change to the DOM state. This can result in poor performance. Learn more about forced reflows and possible mitigations.Unscored
Source
Total reflow time
…scripts/hud?variant=public:156:27(kwenakabobedi.netlify.app)
42 ms
[unattributed]
0 ms

Avoid chaining critical requests by reducing the length of chains, reducing the download size of resources, or deferring the download of unnecessary resources to improve page load.LCPUnscored

Unoptimized hero banner image causing high LCP | Performance | High | Open (Issue #12) |
Navigation buttons missing `aria-label` attributes | Accessibility | Medium | In Progress (Issue #15) |
Missing `meta-description` tag on dashboard page | SEO | Low | Fixed |

## 5. Verification Protocol

Before merging any major Pull Request or deploying to production, follow these steps:
 Open the target page in an **Incognito Window**.
 Open DevTools (`F12` or `Cmd + Option + I`) and navigate to the **Lighthouse** tab.
Select the target mode (**Navigation**) and device type (**Mobile** first, then **Desktop**).
 Click **Analyze page load**.
Log scores and new action items into this document 