!SLIDE 
# The greatest refactoring in the history of mankind. Maybe. #
## (AKA - rewriting the order importer) ##

!SLIDE bullets incremental
# Bullet Points #

* first point
* second point
* third point

!SLIDE

foo bar baz

    @@@ perl
    sub find_foos {
        my ( $self, @list ) = @_;

        my @foos = grep { /foo/ } @list;

        return @foos;
    }
