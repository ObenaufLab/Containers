# Copyright (c) 2018 Tobias Neumann.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM ubuntu:18.04

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

ENV PATH="/centrifuge-1.0.4-beta/ncbi-blast-2.7.1+/bin/:${PATH}"

# binutils is required to run opencl programs
RUN buildDeps='git wget gcc g++ make zlib1g-dev ca-certificates' \
    runDeps='unzip libidn11' \
    && set -x \
    && apt-get update && apt-get install -y $buildDeps $runDeps --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && wget https://github.com/infphilo/centrifuge/archive/v1.0.4-beta.tar.gz \
    && tar xvfz v1.0.4-beta.tar.gz \
    && cd centrifuge-1.0.4-beta \
    && wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.7.1+-x64-linux.tar.gz \
    && tar xvfz ncbi-blast-2.7.1+-x64-linux.tar.gz \
    && make \
    && make install prefix=/usr/local \
    && apt-get purge -y --auto-remove $buildDeps