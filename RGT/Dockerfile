# Copyright (c) 2019 Tobias Neumann.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM ubuntu:18.04

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

ARG VERSION_ARG

# binutils is required to run opencl programs
RUN buildDeps='git wget gcc g++ libc6-dev make zlib1g-dev python-pip python-dev python-distribute python-pip libbz2-dev liblzma-dev' \
    runDeps='python binutils unzip' \
    && set -x \
    && apt-get update && apt-get install -y $buildDeps $runDeps --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && pip install cython numpy scipy setuptools wheel pyBigWig==0.3.12 \
    && pip install RGT \
    && apt-get purge -y --auto-remove $buildDeps
