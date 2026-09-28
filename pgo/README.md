# Raspberry Pi 5 PGO profiles

Raw clang profiles (`*.profraw`) from an instrumented build (`pi5_build.yml`, `pgo=generate`),
recorded on a Raspberry Pi 5 while playing representative titles. `pgo=use` merges every
`*.profraw` here with the same clang version and builds against the result.

Record on the Pi with `LLVM_PROFILE_FILE=/path/armsx2-%p-%m.profraw`, exit the emulator normally
(the profile is written at exit, so a SIGKILL loses it), then commit the files here.

Profiles must come from the same clang major version as the `use` build, and from a commit close
to it: functions whose code has changed since recording are simply left unoptimised.
