# You may redistribute this program and/or modify it under the terms of
# the GNU General Public License as published by the Free Software Foundation,
# either version 3 of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

add_library(cjdns-admin
    Admin.c
    AuthorizedPasswords.c
)
target_link_libraries(cjdns-admin
    crypto
    cjdbenc_StandardBencSerializer
)

add_library(cjdns-admin-logger
    AdminLog.c
)
target_link_libraries(cjdns-admin-logger cjdns-admin)

add_library(cjdns-admin-client
    AdminClient.c
    Configurator.c
)
target_link_libraries(cjdns-admin-client
    crypto
    cjdbenc_StandardBencSerializer
    cjdns-util-platform-socket
)

add_subdirectory(testframework)
add_subdirectory(angel)

enable_testing()
add_subdirectory(test)
