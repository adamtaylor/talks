!SLIDE 
# The greatest refactoring in the history of mankind. Maybe. #
## (AKA - rewriting the order importer) ##

!SLIDE bullets incremental
# What is the order importer? #

* processes orders from the websites (lots $$$)
* a beast
* hard to maintain/understand

!SLIDE bullets incremental
# Order Importer v2 #

* XT::Order::Parser
* XT::Order::Role::Parser
* XT::Order::Parser::PublicWebsiteXML
* XT::Order::Parser::IntegrationServiceJSON
* XT::Data::Order
* XT::Order::Importer

!SLIDE
# XT::Order::Parser #

    @@@ perl
    sub build_parser {
        my ( $class ) = shift;

        # foo
    }

!SLIDE
# XT::Order::Roles::Parser #

    @@@ perl
    package XT::Order::Roles::Parser;
    use Moose::Roles;

    requires 'can_parse';
    requires 'parse';
    1;

!SLIDE
    @@@ perl
    package XT::Order::Importer

    sub import_orders {
        my ( $self, $data ) = @_;

        my $parser = XT::Order::Parser->new(
            data => $data
        );

        foreach ( $data->findnodes('ORDER') ) {
            my $order = $parser->parse( $_ );
            $order->digest();
        }
    }
