# Copyright (c) 2019 Tobias Neumann.
#
# You should have received a copy of the GNU Affero General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM continuumio/miniconda:4.7.10

MAINTAINER Tobias Neumann <tobias.neumann.at@gmail.com>

RUN set -x \
	&& conda config --add channels defaults \
	&& conda config --add channels bioconda \
	&& conda config --add channels conda-forge \
	&& conda create --prefix /nucleoatac -y nucleoatac=0.3.4 openssl=1.0 \
	&& conda clean -a

ENV PATH /nucleoatac/bin:$PATH
