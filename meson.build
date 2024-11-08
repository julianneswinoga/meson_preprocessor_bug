project('my_project', 'c')

preprocesssed_lscript = meson.get_compiler('c').preprocess(
    'lscript.ld',
    output: '@BASENAME@.pp.ld',
)[0]

linker_script_tgt = custom_target(
    'lscript',
    input: preprocesssed_lscript.full_path(),
    output: '@BASENAME@.strip.ld',
    command: [files('strip_lscript.sh'), '@INPUT@', '@OUTPUT@'],
    depends: [preprocesssed_lscript],
)
linker_script_dep = declare_dependency(sources: [linker_script_tgt])
output_file = linker_script_tgt.full_path()
add_project_link_arguments(['-T', f'@output_file@'], language: 'c')

executable('exe', ['main.c'], dependencies: [linker_script_dep])
