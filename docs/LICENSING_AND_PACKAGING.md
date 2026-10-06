# Licensing, Provenance, Packaging and Credit Boundary

This integration sits across multiple independently authored works. Their rights and notices must not be collapsed into one assumed licence.

## 1. PWCG foundation — Patrick Wilson

**PWCG+ is based on and modifies Pat/Patrick Wilson's Pat Wilson Campaign Generator (PWCG).** PWCG+ must always be described as a community enhancement/derivative based on PWCG, not as an independently originated campaign generator.

The frozen upstream source used by PWCG+ is `PWCGDeveloper/PWCGCampaign` at commit `9d81519059d8176a7e621b61e42b649d27a080b9`.

Repository audit found no project-root `LICENSE`, `LICENCE`, `COPYING` or `NOTICE` file in that frozen tree. Public availability of source and invitations to work on it are evidence that modification/development is welcomed, but **they are not a substitute for a formal software licence and must not be described as MIT/GPL/public-domain permission**.

The PWCG+ project separately sought Patrick Wilson's explicit permission to modify PWCG and distribute PWCG+ as a free community enhancement with full credit. Preserve the actual permission correspondence/evidence when received/available; do not broaden its scope beyond what Pat actually granted.

Until that permission evidence is captured verbatim in the release-rights record, public source availability alone must not be represented as a complete standalone redistribution licence.

Required prominent credit in PWCG+ releases/documentation:

> PWCG+ is a community enhancement based on Pat Wilson's Campaign Generator (PWCG). The original PWCG and the substantial underlying campaign-generation work are by Patrick Wilson. PWCG+ is not presented as a replacement claim of authorship over PWCG.

Do not remove original PWCG copyright/author attribution present in files, UI, documentation or packaged resources.

## 2. IL-2 Campaign Tracker / il2_debrief — Alexander Bleiholder (Arrow_1974)

The Campaign Tracker parser remains an external program. PWCG+ must not copy or translate its parser source merely to avoid the external-process boundary.

Based on permission/requirements supplied by Alexander Bleiholder for this integration, PWCG+ release packaging that bundles the analyser must include the applicable `LICENSE` for `il2_debrief`, the `LICENSE-mlg2txt` MIT notice for the Ian Caulfield/Murleen converter, and short IL-2 Campaign Tracker credit/source attribution.

The supplied executables were described by the upstream author as code-signed under publisher **Alexander Bleiholder**. Preserve supplied binaries rather than rebuild/re-sign them under PWCG+ unless separately agreed.

## 3. Other PWCG+ third-party material

PWCG+ also carries separate provenance obligations for other incorporated material. Those permissions/licences remain independent of both PWCG and Arrow's analyser. A release must preserve the applicable author credit, permission evidence and licence/notice for each included component.

Known project policy includes explicit attribution/provenance tracking for community material such as Kraut1 Wingmen Warning material and Off_Winters BoB/Spitfire Mk.I material, plus third-party Java/runtime dependencies. Do not infer that permission for one component covers another.

Do not package extracted/proprietary IL-2 assets merely because their paths or formats are known.

## 4. Release rule

Before any public PWCG+ binary/package:
1. preserve Pat Wilson/PWCG foundation credit and the exact permission provenance supporting modification/redistribution;
2. preserve original notices already carried by PWCG;
3. include every required third-party licence/notice/credit for files actually distributed;
4. include Arrow analyser licences/notices if its binaries are bundled;
5. perform a file-by-file provenance scan of the actual distributable, not only the source repository;
6. do not assign a blanket PWCG+ licence that purports to relicense Pat's or other contributors' work beyond the rights actually granted.

This interoperability repository does not redistribute the analyser executables at initialization and does not itself grant rights over PWCG, Campaign Tracker, IL-2 assets or third-party material.
