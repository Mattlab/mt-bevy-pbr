# Mountain Tycoon focused PBR package

This repository preserves the registry-normalized `bevy_pbr` 0.20.0 package, including its original MIT and Apache licenses and upstream source metadata. It is not an official Bevy release or a full engine fork.

- Official upstream: https://github.com/bevyengine/bevy
- Upstream source commit: `b3bdd75becaffe9a16677cf5bae5bd6d198f052b`, `crates/bevy_pbr`
- Registry package checksum: `fb760932d1e683e7c00011f5c99e4e1cc893646a3a7b7224da6daf9bfa94853d`
- Exact package import commit: `63b55d1360ef2c060ba60a34e6f00f14ec088f16`
- Consumer/repair authority: Mountain Tycoon task 2.145

The only runtime patch defers atmosphere environment probe bind-group creation until its five uniform buffer bindings are available. An initially inactive/withheld camera may legitimately have atmosphere settings and LUTs before an extracted view allocates transform uniforms. The guard preserves the existing LUT/probe producer lifecycle and does not weaken camera admission.

Candidate patch requires independently reviewed source and actual cold-start, warm-suspension/reactivation and generated-environment GPU checks before adoption. No upstream submission or acceptance is claimed. Replace this focused patch when an upstream fix passes the same regression.
