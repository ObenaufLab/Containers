# Copyright (c) 2019 Tobias Neumann.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM combinelab/salmon:0.12.0

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

RUN buildDeps='wget ca-certificates make g++' \
    runDeps='zlib1g-dev libncurses5-dev unzip gcc' \
    && set -x \
    && apt-get install -y $buildDeps $runDeps --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && wget https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2 \
    && tar xvfj samtools-1.9.tar.bz2 \
    && cd samtools-1.9 \
    && ./configure --prefix=/usr/local/ \
    && make \
    && make install \
    && apt-get purge -y --auto-remove $buildDeps
