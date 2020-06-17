# Copyright (c) 2019 Tobias Neumann.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM ubuntu:18.04

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

ENV PATH=$PATH:/samtools-1.2/:/bamgineer/src/

RUN buildDeps='git wget gcc g++ make zlib1g-dev ca-certificates libncurses5-dev python-dev' \
    runDeps='unzip libidn11 bedtools vcftools python-pip python openjdk-8-jre less' \
    && set -x \
    && apt-get update && apt-get install -y $buildDeps $runDeps --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && wget https://github.com/samtools/samtools/releases/download/1.2/samtools-1.2.tar.bz2 \
    && tar xjvf samtools-1.2.tar.bz2 \
    && cd samtools-1.2 \
    && make \
    && make install \
    && cd / \
    && wget https://github.com/statgen/bamUtil/archive/master.tar.gz \
    && tar -xzf master.tar.gz \
    && cd bamUtil-master \
    && make cloneLib \
    && make \
    && make install INSTALLDIR=/bamUtil-install \
    && cd / \
    && wget https://github.com/biod/sambamba/releases/download/v0.6.7/sambamba_v0.6.7_linux.tar.bz2 \
    && tar xjf sambamba_v0.6.7_linux.tar.bz2 \
    && chmod ugo+x sambamba \
    && wget https://faculty.washington.edu/browning/beagle/beagle.09Nov15.d2a.jar \
    && chmod ugo+x beagle.09Nov15.d2a.jar \
    && wget https://github.com/broadinstitute/picard/releases/download/2.21.4/picard.jar \
    && chmod ugo+x picard.jar \
    && pip install setuptools \
    && pip install wheel \
    && pip install markerlib \
    && pip install distribute \
    && pip install pysam==0.8.4 pybedtools PyVCF==0.6.7 pathos pandas \
    && git clone https://github.com/pughlab/bamgineer.git
