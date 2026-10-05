.. change::
    :tags: bug, postgresql
    :tickets: 1504

    Fixed bug where :meth:`.Operations.alter_column` against a PostgreSQL
    identity column would render an incomplete, invalid ``ALTER TABLE ...
    ALTER COLUMN`` statement with no clause at all when the given
    :class:`~sqlalchemy.schema.Identity` options did not differ from the
    existing identity options.  A clear :class:`~sqlalchemy.exc.CompileError`
    is now raised instead, consistently in both offline ``--sql`` rendering
    and online execution.
