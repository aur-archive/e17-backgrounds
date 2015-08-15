# Contributor: Nicky726 (nicky726 <at> gmail <dot> com)
pkgname=e17-backgrounds
pkgver=20130331
pkgrel=1
pkgdesc="Backgrounds for E17 from exchange.enlightenment.org"
arch=('any')
url="http://exchange.enlightenment.org/theme/index/theme_group_id/4/"
license=('Unknown')
depends=('enlightenment17')
makedepends=('wget')
source=()
md5sums=()

# Base URL for the backgrounds.
_backgroundsbase="http://exchange.enlightenment.org/theme/get"

# Array of "id:name" values,
# where id is the theme id at http://exchange.enlightenment.org/.
# Use '_' instead of ' ' in names;
# they will be replaced when printed to stdout.

_backgrounds=(
1444:Avrien
1284:Black_Stains
2074:Blast
904:Blue_Eyed
1474:C2D3
1534:Circuit
1464:Colors_of_freedom
1294:Coreline
1454:E17_Pong
1304:E17_Ripple
1274:E17_Rising
894:Erthviews
964:Endurance
944:Enrotacion
984:E_Fingertips
1384:Gold_Red
1414:Gentoo
334:Grunge_Negative
1504:Handamade
1014:Hoodshot
1524:India
344:Inspire
1544:Just_Debian
1374:Ladybug
1264:Layered_Sky
1354:Leftalone_Houses
1394:Matrix_Rad
1424:Multipleballs
2134:Muse
1584:Nixie
2124:Nude
1434:Paddleballs
994:Reflection
1344:Road_to_Enlightenment
1484:Savrien
634:Sikpaper
364:Simply_White
1514:Squares_Letters
1404:Tamanu
1494:The_Awakening
2114:The_Mistery_of_Picaso
914:Tokio_Nightlife
1924:Tux_Factory
1554:Wannplay
1324:White
1334:White_Fortune
1364:White_Carbon
2194:Portrait_of_Olga
2323:eRusty
2313:eDrailing
2343:Ladybug_rock_dark
2553:Zeitgeist
2583:Laughing_Man
2593:Laughing_Man_Alternate
2667:Elegance
)


package() {
  cd ${srcdir}
  # Get the backgrounds
  for _background in ${_backgrounds[@]} 

  do

    # Separate name and background id.
    _name=${_background#*:} # Remove background "id:"
    _name=${_background//_/ } # Replace '_' by ' '
    _id=${_background%%:*} # Remove theme ":name"

    echo
    echo
    echo "----------------------------------------------------------------"
    echo "*** Downloading background '${_name}'..."
    echo

    # Upstream sends themes under the numerical code, missuse -O to workaround
    wget -O "${_background#*:}.edj" -c "${_backgroundsbase}/${_id}" ||
    echo 2>&1 "### Error downloading background '${_name}'."

  done

  # Prepare package directory structure
  install -m755 -d "${pkgdir}/usr/share/enlightenment/data/backgrounds"

  # Install the edjs
  install -m644 ${srcdir}/*.edj "${pkgdir}/usr/share/enlightenment/data/backgrounds"
}
