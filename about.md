---
layout: default
title: About
order: 2
permalink: /about/
---

# About me...
I am a MSc graduate in Physics at University of Turin, specialising in silicon detectors for high energy physics experiments. I’m also a tech passionate and a (basic) programmer.

## Academic experience
<ul style="list-style: none; padding-left: 0;">
  <li><span style="margin-right: 0.5em;">⚛️</span> <a href="https://www.fisicamagistrale.unito.it/do/home.pl"><em>MSc Degree in Physics</em></a> - <em>University of Turin</em> (2022 - 2025)<br>
    I've specialized in various aspects of experimental particle physics (simulation, event reconstruction and analysis, detector characterisation, electronics). My 
    main focus has been about R&D of silicon detectors with improved time resolution and radiation tolerance for future collider experiments.
    <ul style="list-style: none; padding-left: 1.5em;">
      <li><span style="margin-right: 0.5em;">📜</span> Thesis: "Testing towards the qualification of the detector modules of the CMS Endcap Timing Layer"</li>
      <li><span style="margin-right: 0.5em;">🎓</span> Grade: 110/110 cum laude</li>
    </ul>
  </li>
  <br>
  <li><span style="margin-right: 0.5em;">⚛️</span> <a href="https://fisica.campusnet.unito.it/do/home.pl"><em>BSc Degree in Physics</em></a> - <em>University of Turin</em> (2019 - 2022)
    <ul style="list-style: none; padding-left: 1.5em;">
      <li><span style="margin-right: 0.5em;">📜</span> Thesis: "Characterization and data analysis on resistive silicon detectors"</li>
      <li><span style="margin-right: 0.5em;">🎓</span> Grade: 108/110</li>
    </ul>
  </li>
</ul>

## Working experience 
<ul style="list-style: none; padding-left: 0;">
  <li><span style="margin-right: 0.5em;">☀️</span> <a href="https://www.desy.de/f/students/summer_home_2024_final.html"><em>Summer Research Student</em></a> - <em>DESY Hamburg</em> (07/2024 - 09/2024)<br>
    Working in the ATLAS ITk Strip End-Cap division, with a focus on Petal & System Test.<br>
    Main activities included the operation of a monitoring and interlock system based on an Arduino microcontroller for a coldbox setup.<br>
    Worked on both the electronic and coding aspects of the project.
  </li>
  <br>
  <li><span style="margin-right: 0.5em;">🔭</span> <em>Laboratory Assistant</em> - <em>University of Turin</em> (03/2024 - 04/2024)<br>
    Laboratory assistant for the course <a href="https://fisica.campusnet.unito.it/do/corsi.pl/Show?_id=e34b">Introduction to Nuclear and Subnuclear Physics</a> of the BSc Degree in Physics.<br>
    The main activity was to help the students of the laboratory with experiments involving SiPM and scintillators for cosmic ray detection.
  </li>
  <br>
  <li><span style="margin-right: 0.5em;">👩‍🏫</span> <em>Math and Science Tutor</em> - <em>University of Turin</em> (01/2021 - 06/2021)<br>
    Tutor for the project <a href="https://compitiacasa.i-learn.unito.it/">Compiti@Casa</a> (translation: Homework@Home).<br>
    Helping students from middle school in math and science to achieve more independence while studying and doing homework at home.<br>
    Focus on addressing problems and gaps related to e-learning during the COVID-19 pandemic.
  </li>
</ul>

## Other experiences
<ul style="list-style: none; padding-left: 0;">
  <li><span style="margin-right: 0.5em;">:clipboard:</span> <a href="https://www.desy.de/f/students/summer_home_2024_final.html"><em>PIXEL 2024 Conference</em></a> - <em>Strasbourg</em> (18/11/2024 - 22/11/2024)<br>
    Presented the poster "Thin LGADs as radiation-resilient sensors for 4D tracking" at the <em>Eleventh International Workshop on Semiconductor Pixel Detectors for Particles and Imaging (Pixel2024)</em>.
  </li>
</ul>

## Publications and Proceedings
<div id="orcid-publications">Loading publications...</div>

<script>
const orcidId = "0009-0005-8595-1570";
const container = document.getElementById("orcid-publications");

const abbreviations = {
  "Physical Review Letters": "Phys. Rev. Lett.",
  "Nature Communications": "Nat. Commun.",
  "Journal of Instrumentation": "J. Instrum.",
  "Nuclear Instruments and Methods in Physics Research Section A: Accelerators, Spectrometers, Detectors and Associated Equipment": "Nucl. Instrum. Methods Phys. Res., Sect. A"
};

function formatAuthors(contributors) {
  if (!Array.isArray(contributors) || contributors.length === 0) return "";

  const names = contributors.map(c => {
    // Try credit_name first
    if (c?.["credit-name"]?.value) return c["credit-name"].value;

    // Otherwise try contributor-name fields
    const given = c?.["contributor-name"]?.["given-names"]?.value;
    const family = c?.["contributor-name"]?.["family-name"]?.value;

    if (given || family) return [given, family].filter(Boolean).join(" ");

    return ""; // fallback
  }).filter(Boolean);

  if (names.length === 0) return "";

  if (names.length > 3) return names.slice(0, 3).join(", ") + " <em>et al.</em>";
  return names.join(", ");
}


function extractDOI(externalIds) {
  if (!externalIds || !externalIds["external-id"]) return null;
  const doiEntry = externalIds["external-id"].find(eid =>
    eid["external-id-type"]?.toLowerCase() === "doi"
  );
  if (!doiEntry) return null;
  return "https://doi.org/" + doiEntry["external-id-value"];
}

fetch(`https://pub.orcid.org/v3.0/${orcidId}/works`, {
  headers: { "Accept": "application/vnd.orcid+json" }
})
.then(res => res.json())
.then(data => {
  const works = data.group || [];
  if (works.length === 0) {
    container.innerHTML = "No publications found.";
    return;
  }

  return Promise.all(works.map(group => {
    const summary = group["work-summary"]?.[0];
    const putCode = summary?.["put-code"];
    return fetch(`https://pub.orcid.org/v3.0/${orcidId}/work/${putCode}`, {
      headers: { "Accept": "application/vnd.orcid+json" }
    }).then(res => res.json());
  }));
})
.then(details => {
  if (!details) return;

  // Sort by year
  details.sort((a, b) => {
    const aYear = parseInt(a?.["publication-date"]?.year?.value || "0");
    const bYear = parseInt(b?.["publication-date"]?.year?.value || "0");
    return bYear - aYear;
  });

  container.innerHTML = "<ul>" + details.map(entry => {
    console.log(entry);  // <-- DEBUG: inspect structure

    const title = entry?.title?.title?.value || "Untitled";
    const authors = formatAuthors(entry?.contributors?.contributor);
    const rawjournal = entry?.["journal-title"]?.value || "";
    const journal = abbreviations[rawjournal] || rawjournal;
    const year = entry?.["publication-date"]?.year?.value || "";
    const doi = extractDOI(entry?.["external-ids"]);
    const url = doi || entry?.url?.value;

    return `<li>
      <strong>${title}</strong><br>
      ${authors}<br>
      <em>${journal}</em>${year ? `, ${year}` : ""}<br>
      ${url ? `<a href="${url}">${doi ? "DOI" : "Link"}</a>` : ""}
    </li>`;
  }).join("") + "</ul>";
})
.catch(err => {
  console.error("Error fetching publications:", err);
  container.innerHTML = "Error loading publications.";
});
</script>
