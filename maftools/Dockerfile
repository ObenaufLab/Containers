# Copyright (c) 2019 Tobias Neumann.
#
# 
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM rocker/tidyverse:3.6.0

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

ARG VERSION_ARG

# binutils is required to run opencl programs
RUN buildDeps='libbz2-dev liblzma-dev' \
    && set -x \
    && apt-get update && apt-get install -y $buildDeps --no-install-recommends \
    && rm -rf /var/lib/apt/lists/* \
    && Rscript -e 'install.packages(c("mclust","pheatmap"), repos="https://cran.wu.ac.at/")' \
       -e 'install.packages("BiocManager")' \
       -e 'BiocManager::install("maftools",update = FALSE)' \
       -e 'BiocManager::install("BSgenome.Hsapiens.UCSC.hg38",update = FALSE)' 