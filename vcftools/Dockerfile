# Copyright (c) 2018 Tobias Neumann.
#
# 
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM ubuntu:18.04

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV DEBCONF_NONINTERACTIVE_SEEN true

# binutils is required to run opencl programs
RUN buildDeps='git wget gcc g++ libc6-dev make cmake zlib1g-dev bzip2 libncurses-dev libbz2-dev liblzma-dev' \
    runDeps='binutils unzip tabix vcftools samtools' \
    && echo "tzdata tzdata/Areas select Europe" > /tmp/preseed.txt; \
    echo "tzdata tzdata/Zones/Europe select Berlin" >> /tmp/preseed.txt; \
    debconf-set-selections /tmp/preseed.txt \
    && set -x \
    && apt-get update && apt-get install -y $buildDeps $runDeps --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get purge -y --auto-remove $buildDeps