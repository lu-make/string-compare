# Zwei Strings vergleichen und rekursiv Ähnlichkeiten ermitteln. (Langsam)
# Autor: Lukas Keeve

use strict;
use warnings;
use diagnostics;
	
our @score;
our @str0;
our @str1;

# Funktion, die SCORE ermittelt.
# Eingabe: Zwei Strings $u, $v
# Rückgabe: Ermittelter Score in Prozent
sub compare($$){
	my ($u, $v) = @_;
	push (@str0, $u);
	push (@str1, $v);
	my $str0_ref = \@str0;
	my $str1_ref = \@str1;
	list($u, $str0_ref);
	list($v, $str1_ref);
	foreach (@str0){
			push(@score, (search($v, $_)));
			print(" " . $score[$#score] . "\n");
		}
	foreach (@str1){
			push(@score, (search($u, $_)));
			print(" " . $score[$#score] . "\n");
		}
	my $score = 0;
	my $total = ($#score + 1);
	foreach my $i (@score){
		$score += $i;
	}
	my $p = (($score / $total) * 100);
	print("@score\n$score / $total => $p%\n");
	return $p;
}

# Rekursive Funktion, welche String in Substrings teilt und diese in einer Liste speichert.
# Eingabe: String $s, Array-Referenz (@str1 oder @str2)
# Rückgabe: sobald Mindestlänge unterschritten ist und Substrings nicht mehr gespalten werden können
sub list($$){
	my $l;
	my $s = $_[0];
	my $arr_ref = $_[1];
	# print("Substrings: @{$arr_ref}\n");
	# print("List " . $s . "\n");
	$l = length($s);
	if ($l <= 2){ # Je höher die Mindestlänge, desto schneller wird der Algorithmus (mit verringerter Genauigkeit bei sehr kurzen Strings).
		return;
	}
	my @div = divide($s, $l);
	foreach (@div) {
		push(@$arr_ref, $_);
		&list ($_, $arr_ref);
	}
}

# Funktion um Substring in anderem String zu suchen
# Eingabe: Zwei Strings $u und $v
# Rückgabe: 1 falls $v in $u enthalten ist, sonst 0
sub search($$) {
	my ($u, $v) = @_;
	print("\"" . $u . "\" - \"" . $v . "\" ");
	return 1 if (index($u, $v) > -1);
	return 0;
}

# Funktion, um String in zwei Substrings zu halbieren
# Eingabe: String $s, Länge $len
# Rückgabe: Zwei Strings $s0 und $s1
sub divide($$) {
	my ($s, $len) = @_;
	my $s0 = substr($s, 0, ($len / 2));
	my $s1 = substr($s, ($len / 2), $len);
	# print("Teile \"" . $s . "\" -> \"" . $s0 . "\" - \"" . $s1 . "\"\n");
	return ($s0, $s1);
}

### Bei Aufruf in Kommandozeile ###

## Aufruf mit Argumenten ##

#our ($input1, $input2) = @ARGV;
#compare($input1, $input2) if ($input1 and $input2);
#print "Geben Sie zwei Strings an." unless ($input1 and $input2);

## Aufruf mit Nutzereingabe ##

# print "String 1: ";
# our $input1 = <STDIN>;
# chomp $input1;
# print "String 2: ";
# our $input2 = <STDIN>;
# chomp $input2; 
# compare($input1, $input2);
