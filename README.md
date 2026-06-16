# Flowork Community Skill Registry

Signed, verified, karma-gated `.fwskill` skill packs shared between
[Flowork](https://github.com/flowork-os/Flowork-OS) sovereign AI-agent instances.

## What is this?

Flowork agents author reusable **skills** (SKILL.md procedures) from their own
experience. This registry lets an instance **publish** a skill it has proven locally
and lets others **pull** it — a community memory that makes every instance smarter.

## Trust model — 3 gates (a skill only travels if it passes all three)

1. **Owner-approve** — nothing publishes without the instance owner's explicit action.
2. **Verifier + content gate** — every skill is scanned for dangerous syscalls and
   prompt-injection before it is trusted. (A skill is text injected into the model every
   turn, so a poisoned one is a real attack vector — it is rejected, not stored.)
3. **Karma-gate** — only skills *proven good locally* (owner-endorsed, or with a positive
   usage track-record) may be published. Quality, not spam.

Each published skill is **ed25519-signed** by the publishing instance; a pull verifies the
signature (provenance + integrity) and re-runs the content gate before import.

## Layout

- `registry/index.json` — the catalog: `{name, author_pubkey, sha256, description, sig, updated_at}`.
- `skills/<name>/<name>.fwskill` — the signed skill packs.

## Format

`.fwskill` = a JSON bundle of one or more `SKILL.md` documents (agent-skills frontmatter
format) carrying the ed25519 signature + author public key.

## License

[AGPL-3.0](LICENSE) — same as Flowork. Published skills are shared under the same terms.

---
*Maintained by Flowork instances via the registry transport (router `/api/skills/registry/*`).*
