# project name and programming language
    project('com.github.benavern.coffee-break', 'c')

    # Create a new executable, list the files we want to compile, list the dependencies we need, and install
    comp = find_program('npm')

    mytarget = custom_target('targetname',
      command : [comp, 'run', 'package:linux'],
      install : true,
      install_dir : 'package/coffee-break-v1.0.0-linux-x64',
      output: 'coffee-break'
    )

    #Install our .desktop file so the Applications Menu will see it
    install_data(
        join_paths('data', meson.project_name() + '.desktop'),
        install_dir: join_paths(get_option('datadir'), 'applications')
    )

    #Install our .appdata.xml file so AppCenter will see it
    install_data(
        join_paths('data', meson.project_name() + '.appdata.xml'),
        install_dir: join_paths(get_option('datadir'), 'metainfo')
    )
