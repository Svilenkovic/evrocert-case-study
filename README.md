<a href="https://evrocert.rs/"><img src="media/cover.jpg" alt="EVROCERT, home page on a laptop and a phone" width="100%"></a>

# EVROCERT

Site for a Kragujevac certification body, with the ISO standards, the certification process and a public register anyone can search.

**[evrocert.rs](https://evrocert.rs/)** · [Case study (in Serbian)](https://svilenkovic.rs/radovi/evrocert) · [Srpski](README.sr.md)

> [!NOTE]
> Client project. The source code belongs to the client and stays in a private repository. This page describes what I built and how.

<table>
  <tr><td><b>Client</b></td><td>EVROCERT</td></tr>
  <tr><td><b>Industry</b></td><td>Certification of management systems (ISO 9001, 14001, 45001)</td></tr>
  <tr><td><b>Location</b></td><td>Kragujevac, Serbia</td></tr>
  <tr><td><b>Type</b></td><td>Multi-page website with a public register</td></tr>
  <tr><td><b>My role</b></td><td>Redesign, development, migration, hosting and maintenance</td></tr>
  <tr><td><b>Stack</b></td><td>PHP 8.3, SQLite, Drupal (applications and accounts), nginx</td></tr>
</table>

## About the project

EVROCERT certifies management systems and is accredited by ATS, the Serbian accreditation body. Two kinds of visitors come to its site: a company that is thinking about certification and wants to know what it is in for, and a buyer who needs to check whether a supplier's certificate is still valid. I rebuilt the public site around those two questions.

The register took the most care. I moved the public content and the certificate register out of the old Drupal system into a new SQLite database. The import runs through a temporary database in a single transaction and stops if the counts differ from the source (85 organizations and 173 certificates). Status is worked out on the day of the search, so a certificate whose validity date has passed shows as expired even when the old data still marks it as active.

## What I built

- Separate pages for ISO 9001, ISO 14001 and ISO 45001, and the process split into application, two audit stages, an independent decision and surveillance
- A public register searched by organization name or address, with filters for standard and status
- Results put together on the server, so the search also works without JavaScript
- An import that refuses to finish if the numbers differ from the old system; 36 certificates without a matching organization were kept exactly as found
- A content security policy that allows scripts and styles only from the same domain
- Online applications, user accounts and the EIS login left in the existing system until they can move with the same features

## Results

| | Performance | Accessibility | Best practices | SEO |
| :-- | :-: | :-: | :-: | :-: |
| Mobile | 100 | 100 | 100 | 100 |
| Desktop | 100 | 100 | 100 | 100 |

PageSpeed Insights, lab test of the live site, October 2026. Security headers: 6 of 6. HTML validator: no errors. axe accessibility check: no violations. Structured data: `Organization`.

## Screenshots

<table>
  <tr>
    <td width="68%" valign="top"><img src="media/desktop.webp" alt="EVROCERT, home page on a 1440 px screen"></td>
    <td width="32%" valign="top"><img src="media/mobile.webp" alt="EVROCERT, home page on a phone"></td>
  </tr>
</table>

<img src="media/inner-1.webp" alt="Public certificate register with search by name or address">
<sub>Public certificate register with search by name or address</sub>

<img src="media/inner-2.webp" alt="The three standards in the accredited scope, each with its own page">
<sub>The three standards in the accredited scope, each with its own page</sub>

---

<sub>Built by [D. Svilenković](https://svilenkovic.com).</sub>
