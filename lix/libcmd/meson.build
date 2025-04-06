liblix_sources += files(
  'built-path.cc',
  'cmd-profiles.cc',
  'command.cc',
  'common-eval-args.cc',
  'editor-for.cc',
  'installable-attr-path.cc',
  'installable-derived-path.cc',
  'installable-flake.cc',
  'installable-value.cc',
  'installables.cc',
  'legacy.cc',
  'markdown.cc',
  'repl.cc',
  'repl-interacter.cc',
)

libcmd_headers = files(
  'built-path.hh',
  'cmd-profiles.hh',
  'command.hh',
  'common-eval-args.hh',
  'editor-for.hh',
  'enum-traits.hh',
  'installable-attr-path.hh',
  'installable-derived-path.hh',
  'installable-flake.hh',
  'installable-value.hh',
  'installables.hh',
  'legacy.hh',
  'markdown.hh',
  'repl-interacter.hh',
  'repl.hh',
)

libcmd_setting_definitions = files(
  # keep-sorted start
  'settings/default-flake.md',
  # keep-sorted end
)
liblix_generated_headers += custom_target(
  command : [
    python.full_path(),
    '@SOURCE_ROOT@/lix/code-generation/build_settings.py',
    '--kernel', host_machine.system(),
    '--header', '@OUTPUT@',
    '--experimental-features', '@SOURCE_ROOT@/lix/libutil/experimental-features',
    '@INPUT@',
  ],
  input : libcmd_setting_definitions,
  output : 'libcmd-settings.gen.inc',
  install : true,
  install_dir : includedir / 'lix/libcmd',
)

liblix_generated_headers += [
  gen_header.process('repl-overlays.nix', preserve_path_from: meson.current_source_dir()),
]

install_headers(libcmd_headers, subdir : 'lix/libcmd', preserve_path : true)
