# StudentPulse documentation

Integration documentation built with Mintlify. Public pages are MDX files. Site navigation and links are in `docs.json`.

## Preview and checks

Run these commands from this directory:

```bash
mint dev --no-open
mint validate
mint broken-links --check-anchors
```

The preview is normally at http://localhost:3000. Use the URL printed by the CLI if the port is busy.

## Source and scope

The initial content was converted on 15 October 2026 from [StudentPulse V1.5 Documentation — general version, November 2025](https://docs.google.com/document/d/1yJfvTaHZHtvBYVuulM3dlXCyJUEEo-BGluDScIg0kkw/edit).

Related work: [studentpulse/studentpulse.io#3321](https://github.com/studentpulse/studentpulse.io/issues/3321).

The migration includes:

- Integration overview and setup planning.
- Check-in URL parameters, using synthetic identifiers.
- Power BI/Fabric setup, export timing, data model, and all 48 dictionary fields.
- The draft Check-in API, including create, get, delete, and distribution operations.

The source's customer URLs and demo Check-in identifiers were replaced with generic examples. Missing source images were replaced with text and tables. The source's invalid response JSON and unescaped table delimiters were corrected.

Microsoft Teams bot and Microform webhook instructions were omitted from this site because issue #3321 calls for legacy content review. The source document still holds those instructions. This migration does not establish that all Teams integration paths are unavailable.

## Review before publication

The content has not been verified against the current application or a live integration. Draft notices are visible in the site. Do not remove them until the relevant checks are complete.

- [ ] Assign a technical owner for each topic and record its verification date.
- [ ] Verify the current export settings path, connector credentials, and nightly export schedule.
- [ ] Verify all field names, types, array serialization, and the answer-level row grain against a sample export.
- [ ] Resolve the source formula `AVG(answer_value_0_100) / 10`; its input field is missing from the dictionary. Do not assume `Reply value` uses that scale.
- [ ] Verify `source`, segmentation ID mapping, locale codes, option handling, and URL encoding with a test Check-in.
- [ ] Confirm any additional exported identifier and its permitted use. Do not claim arbitrary URL parameters become export fields.
- [ ] Verify the API base URL, authentication, and create/delete endpoints.
- [ ] Resolve Get: `/checkin/:uuid` in the summary versus `/checkin/:id` in the detail.
- [ ] Resolve distribution: `/checkin/distribute` in the summary versus `/checkin/reminder` in the detail.
- [ ] Verify the API date format, replacement-variable JSON structure, required fields, nullability, errors, and retry rules.
- [ ] Verify delete parameter placement and the effect on associated data.
- [ ] Verify distribution recipients, delivery channels, and duplicate-send behavior.
- [ ] Add verified Group integration content. It is absent from the supplied document.
- [ ] Add verified UniLogin/Aula content. It is absent from the supplied document.
- [ ] Confirm which Teams content is obsolete before any separate archive or removal work.
- [ ] Add approved StudentPulse logo and favicon assets. Existing starter SVG assets remain unused.
- [ ] Review the pages before sharing with TimeEdit.

The Google document's internal revision label is not treated as an API version. `V1.5` follows the source product name; the source base URL uses `/v1/`.

## Editing

AI agents and developers can edit MDX files on a branch. Non-developers can use the Mintlify web editor. Each new public page needs a title, description, and navigation entry.

The repository's `AGENTS.md` requests the Mintlify skill. It is installed locally in `.agents/skills/mintlify` for Codex.

## Publication

Pushing changes to the connected deployment branch triggers Mintlify publication. Keep unverified changes on a review branch. This generation task does not publish the site.
