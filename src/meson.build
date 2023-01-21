pkgdatadir = join_paths(get_option('prefix'), get_option('datadir'), meson.project_name())
moduledir = join_paths(pkgdatadir, 'cuadre_caja')
gnome = import('gnome')

gnome.compile_resources('cuadre_caja',
  'cuadre_caja.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', join_paths(get_option('prefix'), get_option('localedir')))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'cuadre_caja.in',
  output: 'cuadre_caja',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir')
)

cuadre_caja_sources = [
  '__init__.py',
  'main.py',
  'window.py',
]

install_data(cuadre_caja_sources, install_dir: moduledir)
