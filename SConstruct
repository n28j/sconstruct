Mkdir('obj')
Mkdir('bin')

AddOption('--d', action='store_true', dest='user_debug', default=False, help='Build with debug mode enabled')

env = Environment()

# Compiler flags
if GetOption('user_debug'):
    env.AppendUnique(CCFLAGS=['-g3'])
else:
    env.AppendUnique(CCFLAGS=['-Os'])

# Libraries
env.Append(LIBS=[])

# Include directories
env.Append(CPPPATH='.')

env_files = []

for src_file in Glob('*.c'):
    filename = src_file.path.split('/')[-1][:-2]
    env_files.append(env.Object(f'obj/{filename}.o', src_file))

env.Program('bin/main', env_files)

Clean('bin/main', ['bin', 'obj'])
