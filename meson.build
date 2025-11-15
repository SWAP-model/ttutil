project('ttutil', 'fortran', version : '4.2.7', default_options : ['warning_level=0'])

fc = meson.get_compiler('fortran')

# Intel Fortran compiler settings
if fc.get_id() == 'intel'
    add_project_arguments([
        '-O2',
        '-fpscomp', 'general',
        '-warn', 'declarations',
        '-warn', 'unused', 
        '-warn', 'uncalled',
        '-warn', 'interfaces',
        '-save',
        '-init=zero',
        '-fpe0',
        '-fp-model', 'source',
        '-fPIC'
    ], language : 'fortran')
    
    # For Windows cross-compilation with Intel (when needed)
    if host_machine.system() == 'windows'
        add_project_link_arguments(['-static'], language : 'fortran')
    endif
    
# MinGW Fortran compiler settings for Windows cross-compilation
elif fc.get_id() == 'gcc' and host_machine.system() == 'windows'
    add_project_arguments([
        '-O2', 
        '-fPIC',
        '-Wno-line-truncation',
        '-Wno-compare-reals',
        '-std=legacy',
        '-mconsole',
        '-static-libgfortran',
        '-static-libgcc'
    ], language : 'fortran')
    add_project_link_arguments(['-static', '-mconsole'], language : 'fortran')
endif

# Source files in compilation order (matching original Intel script)
f90_sources = [
    'src/ttutilprefs.f90',
    'src/ttutil.f90',
    'src/rdmodulettutil.f90',
    'src/dtnow.f90',
    'src/fatalerr.f90',
    'src/fopengstandard.f90',
    'src/ifindc.f90',
    'src/messini.f90',
    'src/messinq.f90',
    'src/newlinestandard.f90',
    'src/openlogf.f90',
    'src/outar2.f90',
    'src/outdat.f90',
    'src/outsel.f90',
    'src/recread.f90',
    'src/recreadi.f90',
    'src/recreadt.f90',
    'src/upperc.f90'
]

for_sources = [
    'src/addinf.for',
    'src/addint.for',
    'src/addrea.for',
    'src/addref.for',
    'src/addstf.for',
    'src/addstr.for',
    'src/ambusy.for',
    'src/copfl2.for',
    'src/decchk.for',
    'src/decdou.for',
    'src/decint.for',
    'src/decrea.for',
    'src/decrec.for',
    'src/dectim.for',
    'src/delfil.for',
    'src/dtardp.for',
    'src/dtdpar.for',
    'src/dtdpst.for',
    'src/dtfsecmp.for',
    'src/dtfsedp.for',
    'src/dtleap.for',
    'src/dtsys.for',
    'src/entcha.for',
    'src/entdch.for',
    'src/entddo.for',
    'src/entdin.for',
    'src/entdou.for',
    'src/entdre.for',
    'src/entdti.for',
    'src/entdyn.for',
    'src/enthlp.for',
    'src/entint.for',
    'src/entrea.for',
    'src/enttim.for',
    'src/entyno.for',
    'src/extens.for',
    'src/flexist.for',
    'src/flname.for',
    'src/fopens.for',
    'src/getrec.for',
    'src/getun.for',
    'src/getun2.for',
    'src/ifindi.for',
    'src/istart.for',
    'src/iunifl.for',
    'src/lint.for',
    'src/lowerc.for',
    'src/messwrt.for',
    'src/movavr.for',
    'src/notnul.for',
    'src/outcom.for',
    'src/outplt.for',
    'src/parsword.for',
    'src/rchrsrc.for',
    'src/rdacha.for',
    'src/rdador.for',
    'src/rdadou.for',
    'src/rdainr.for',
    'src/rdaint.for',
    'src/rdalog.for',
    'src/rdarea.for',
    'src/rdarer.for',
    'src/rdatim.for',
    'src/rddata.for',
    'src/rddtmp.for',
    'src/rderr.for',
    'src/rderri.for',
    'src/rdfcha.for',
    'src/rdfdor.for',
    'src/rdfdou.for',
    'src/rdfinr.for',
    'src/rdfint.for',
    'src/rdflog.for',
    'src/rdfrea.for',
    'src/rdfrer.for',
    'src/rdfrom.for',
    'src/rdftim.for',
    'src/rdinar.for',
    'src/rdindt.for',
    'src/rdindx.for',
    'src/rdinit.for',
    'src/rdinlv.for',
    'src/rdinne.for',
    'src/rdinqr.for',
    'src/rdinqr2.for',
    'src/rdinqr3.for',
    'src/rdlex.for',
    'src/rdmcha.for',
    'src/rdmdef.for',
    'src/rdmdou.for',
    'src/rdmint.for',
    'src/rdmlog.for',
    'src/rdmrea.for',
    'src/rdmtim.for',
    'src/rdpars.for',
    'src/rdscha.for',
    'src/rdsctb.for',
    'src/rdsdor.for',
    'src/rdsdou.for',
    'src/rdsets.for',
    'src/rdsinr.for',
    'src/rdsint.for',
    'src/rdslog.for',
    'src/rdsrea.for',
    'src/rdsrer.for',
    'src/rdstim.for',
    'src/rdtmp1.for',
    'src/rdtmp2.for',
    'src/reaand.for',
    'src/reanor.for',
    'src/remove.for',
    'src/sfindg.for',
    'src/sortch.for',
    'src/sortin.for',
    'src/str_copy.for',
    'src/swpi4.for',
    'src/ttuver.for',
    'src/unifl.for',
    'src/usedun.for',
    'src/ver4_27.for',
    'src/warning.for',
    'src/words.for',
    'src/wracha.for',
    'src/wradou.for',
    'src/wraint.for',
    'src/wralog.for',
    'src/wrarea.for',
    'src/wratim.for',
    'src/wrinit.for',
    'src/wrscha.for',
    'src/wrsdou.for',
    'src/wrsint.for',
    'src/wrslog.for',
    'src/wrsrea.for',
    'src/wrstim.for'
]

# Combine all sources
all_sources = f90_sources + for_sources

# Create the static library
if host_machine.system() == 'windows' and fc.get_id() == 'gcc'
    # For Windows cross-compilation with MinGW
    library_name = 'ttutil427_windows'
else
    # For native Intel compilation  
    library_name = 'ttutil427'
endif

ttutil_lib = static_library(library_name, all_sources,
    install : true,
    install_dir : 'lib'
)

# Create an include directory with module files
install_subdir('src', install_dir : 'include', strip_directory : true, 
    exclude_files : ['*.for', '*.f90', 'my_compile_ttutil.sh', 'diagnostics.diag'])