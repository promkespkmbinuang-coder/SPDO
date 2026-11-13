# Audit Matrix — Skill, Prompt System, Plugin, Agent Workflow

Gunakan sebagai checklist cakupan, bukan kewajiban mengkritik setiap baris. Tandai PASS, GAP, RISK, NOT_APPLICABLE, atau NOT_VERIFIED beserta bukti.

| Domain | Pertanyaan audit | Bukti |
|---|---|---|
| Intent fidelity | Apakah tujuan pengguna tetap utuh? | Intent brief, requirement trace |
| Role & authority | Apakah tanggung jawab dan izin jelas? | Role matrix, decision rights |
| Objective & tasks | Apakah objective, requirement, task, dependency, acceptance dibedakan? | Objective tree |
| Skill architecture | Apakah modularitas, ownership, trigger, routing, handoff jelas? | Skill map |
| Context & data | Apakah sumber, freshness, variabel, unknown dikelola? | Context/evidence registry |
| Methods | Apakah metode relevan dan dibatasi? | Method blueprint |
| Tool capability | Apakah tool/provider tersedia dan diotorisasi? | Capability record |
| Security & safety | Apakah trust boundary, injection, privacy, secrets, side effects terkendali? | Threat model |
| Failure handling | Apakah exception, retry, fallback, rollback operasional? | Failure matrix |
| Output contract | Apakah hasil dapat divalidasi? | Schema, examples |
| Evidence & logic | Apakah fakta, asumsi, inferensi, kausalitas dipisahkan? | Claim-evidence matrix |
| Compatibility | Apakah perubahan menjaga klien, schema, API, versi? | Compatibility matrix |
| Maintainability | Apakah struktur, docs, changelog, dependencies terpelihara? | Repo inventory |
| Testing | Apakah oracle dan coverage sesuai impact? | Test plan/report |
| Governance | Apakah review, approval, rollback, release gate jelas? | PR/release record |

## Method selection
- First Principles: uji asumsi dasar; bukan solusi universal.
- Systems Thinking: feedback, delay, interdependensi; diagram bukan bukti kausal.
- Issue Tree/MECE: dekomposisi cakupan; jangan klaim sempurna tanpa uji batas.
- Root Cause Analysis: telusuri mekanisme defect; 5 Whys/Fishbone bukan bukti otomatis.
- FMEA: failure modes, effects, controls; RPN butuh skala yang didefinisikan.
- Fault Tree/Bow-tie: jalur top event dan barrier; jangan mengarang probabilitas.
- Premortem: skenario kegagalan kredibel, bukan prediksi.
- Abuse/Misuse Case dan threat modeling: uji penyalahgunaan dan trust boundary.
- Dependency analysis: peta dependensi; bukan bukti seluruh runtime edges.
- Boundary/equivalence testing: uji input dan state transitions.
- Mutation testing: uji sensitivitas test; bukan bukti correctness menyeluruh.
- Comparative analysis: bandingkan opsi dengan kriteria/bobot transparan.

## Severity and confidence
Severity adalah dampak bila masalah terjadi; confidence adalah kekuatan bukti. Jangan gabungkan tanpa model.
- P0: keselamatan, keamanan, data loss, integritas, unauthorized action, pelanggaran mendasar.
- P1: fungsi inti atau release gate tidak dapat dipercaya.
- P2: penurunan kualitas/operasional material.
- P3: masalah minor/kosmetik.
Confidence HIGH (observasi/bukti kuat), MEDIUM (mekanisme dan bukti parsial), LOW (hipotesis), UNKNOWN. Jelaskan apa yang dapat mengubah confidence.
