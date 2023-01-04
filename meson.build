project('lua-zlib', 'c', version : '1.2')

lua_puc_rio_dep = dependency('lua', required : false)
if lua_puc_rio_dep.found()
    lua_dep = lua_puc_rio_dep
    # We get the first 3 characters because we don't want the minor
    # version number.
    lua_version = lua_dep.version().substring(0, 3)
else
    lua_dep = dependency('luajit')
    if lua_dep.version().substring(0, 3) in ['2.0', '2.1']
        lua_version = '5.1'
    else
        error('unknown luajit version: ' + lua_dep.version())
    endif
endif

zlib_dep = dependency('zlib')

shared_library('zlib', 'lua_zlib.c',
    dependencies : [zlib_dep, lua_dep],
    name_prefix : '',
    install_dir : 'lib/lua/' + lua_version,
    install : true,
)
