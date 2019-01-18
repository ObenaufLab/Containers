# Copyright (c) 2018 Tobias Neumann.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM ubuntu:18.04

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

ENV PATH="/samtools-1.3.1/centrifuge-1.0.4-beta/bwa-0.7.17/:/centrifuge-1.0.4-beta/ncbi-blast-2.7.1+/bin/:/seqtk-1.3/:${PATH}"

# binutils is required to run opencl programs
RUN buildDeps='git wget gcc g++ make zlib1g-dev ca-certificates libncurses5-dev' \
    runDeps='unzip libidn11 bedtools' \
    && set -x \
    && apt-get update && apt-get install -y $buildDeps $runDeps --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && wget https://github.com/samtools/samtools/releases/download/1.3.1/samtools-1.3.1.tar.bz2 \
    && tar xjvf samtools-1.3.1.tar.bz2 \
    && cd samtools-1.3.1 \
    && make \
    && make install \
    && wget https://github.com/infphilo/centrifuge/archive/v1.0.4-beta.tar.gz \
    && tar xvfz v1.0.4-beta.tar.gz \
    && cd centrifuge-1.0.4-beta \
    && wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.7.1/ncbi-blast-2.7.1+-x64-linux.tar.gz \
    && tar xvfz ncbi-blast-2.7.1+-x64-linux.tar.gz \
    && make \
    && make install prefix=/usr/local \
    && wget https://github.com/lh3/bwa/releases/download/v0.7.17/bwa-0.7.17.tar.bz2 \
    && tar xjvf bwa-0.7.17.tar.bz2 \
    && cd bwa-0.7.17 \
    && make \
    && cd / \
    && wget https://github.com/lh3/seqtk/archive/v1.3.tar.gz \
    && tar xvfz v1.3.tar.gz \
    && cd seqtk-1.3 \
    && make \
    && apt-get purge -y --auto-remove $buildDeps
