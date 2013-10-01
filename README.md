Teng::Plugin::RowObjectCreationSwitcher - Teng's plugin which enables/disables suppress\_row\_objects with guard object.

# SYNOPSIS

    use MyProj::DB;
    use parent qw(Teng);
    __PACKAGE__->load_plugin('RowObjectCreationSwitcher');

    package main;
    my $db = MyProj::DB->new(dbh => $dbh);
    {
        my $guard = $db->temporary_suppress_object_creation_guard(1); # row object creation is suppressed
        {
            my $guard2 = $db->temporary_suppress_object_creation_guard(1); # row object is created. (isn't suppressed)
            ... # do something
        }
        # dismiss $guard2 (row object creation is suppressed)
        ... # do something
    }
    # dismiss $guard (row object creation is unsuppressed)

# DESCRIPTION

Teng::Plugin::RowObjectCreationSwitcher is plugin for [Teng](http://search.cpan.org/perldoc?Teng) which provides switcher to enable/disable to generate row object.
This switcher returns guard object and if guard is dismissed, status is back to previous.

# METHODS

## $guard = $self->temporary\_suppress\_object\_creation\_guard($bool\_suppress\_row\_objects)

set suppress\_row\_objects and return guard object.  When guard is dismissed, status is back to previous.

# LICENSE

Copyright (C) Takuya Tsuchida.

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.

# AUTHOR

Takuya Tsuchida <tsucchi@cpan.org<gt>
