B=../bin

%:
	$B/ytgloss -f $@-fixparse.txt -g $@-fixgloss.txt $@.txt |\
	$B/ytknown -k $@-known.txt -r $@-rubyonly.txt > $@.yt
	$B/ytruby $@.yt | $B/yt2latex > $@.tex
	uplatex $@.tex > /dev/null
#current version of dviasm can't handle uplatex output
#	$B/dvicleanruby $@.dvi
	dvipdfmx -q $@.dvi
	$B/ytvocab -t $@.aux -l $@.yt > $@-vocab.tex
	uplatex $@-vocab.tex > /dev/null
	dvipdfmx -q $@-vocab.dvi
	$B/ytruby $@.yt | $B/yt2odt -o $@.odt
	$B/ytruby $@.yt | $B/yt2word > $@.doc
	$B/yt2html $@.yt > $@.html

clean:
	@rm -f *.yt- *.yt *.tex *.aux *.log *.dvi *.dvi* *.dump *~

realclean: clean
	@rm -f *.pdf *.odt *.doc *.html


