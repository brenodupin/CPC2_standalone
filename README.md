CPC2 standalone
====

* 2025-10-25 19:30 BRT Breno Dupin / Matheus Sanita
   - Add `putative_peptide` output to `--ORF` flag
   - Add `--debug` flag, that will output to stderr about `mRNA_translate()` and `calculate_potential()`
   - Update README.md with new features

* 2025-10-22 11:30 BRT Breno Dupin / Matheus Sanita
   - Rebase [python3 changes](https://github.com/gao-lab/CPC2_standalone/releases/tag/v1.0.1) from HyperOdin into repository
   - Update `_reversecompliment()` basepair with ambiguous base pairing
   - Add `putative_peptide` output to `--ORF` flag (same as [CPC2_output_peptide.py](https://github.com/gao-lab/CPC2_standalone/blob/53ba517309aad8ddb1054c13ea93d6781ce3dfe8/bin/CPC2_output_peptide.py))

* 2019-11-23 15:30, Yang Ding
   - Now CPC2 supports both Python 2 and Python 3 (thanks for help from HyperOdin)

1 Pre-requisite:
----
a. Biopython package: a local version could be downloaded from
http://biopython.org/wiki/Download

	pip install biopython

2 Install
----
a. Clone this repo:

	git clone https://github.com/brenodupin/CPC2_standalone.git

> [!NOTE]
> This is a fork, with some modifications, of the original CPC2_standalone repository from Gao Lab. The original repository is available at
> https://github.com/gao-lab/CPC2_standalone

b. Build third-part packages: 

	cd CPC2_standalone
	export CPC_HOME="$PWD"
	cd libs/libsvm
	gzip -dc libsvm-3.18.tar.gz | tar xf -
	cd libsvm-3.18
	make clean && make

3 Run the predict
----
	cd $CPC_HOME
	bin/CPC2.py -i (input_seq) -o (result_in_table)
example: bin/CPC2.py -i data/example.fa -o example_output

4 Output result
----
The result is in table format (plain text delimited by tab).

Default output:<br>
#ID	transcript_length	peptide_length	Fickett_score	pI	ORF_integrity	coding_probability	label

Set '--ORF' to output strand, start position and the putative peptide of longest ORF:<br>
#ID	transcript_length	peptide_length	Fickett_score	pI	ORF_integrity	ORF_Strand	ORF_Start	putative_peptide	coding_probability	label

Contact
----
>This is a fork version maintained by Breno Dupin

>For any questions, just open an issue on this repository.
