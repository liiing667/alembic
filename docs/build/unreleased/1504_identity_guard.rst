.. change::
    :tags: bug, postgresql
    :tickets: 1504

    Fixed bug where :meth:`.Operations.alter_column` against a PostgreSQL
    identity column could still render an incomplete, invalid ``ALTER TABLE
    ... ALTER COLUMN`` statement with no clause at all, or fail with an
    uninformative ``AssertionError``, when the identity options to alter
    did not differ from ``existing_server_default`` or when
    ``existing_server_default`` was not itself an ``Identity`` construct.
    A clear :class:`sqlalchemy.exc.CompileError` is now raised in both
    cases, consistently in offline ``--sql`` and online execution modes.
