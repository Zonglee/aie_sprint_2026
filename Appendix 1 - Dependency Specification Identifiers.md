| Identifiers |         Name         | Usage                                                                                                              |
| :---------: | :------------------: | :----------------------------------------------------------------------------------------------------------------- |
|      ^      |  Caret Requirement   | Allows any upgrade before next major version.<br>e.g. `^2.1.0` = \[2.1.0, 3.0.0\)                                  |
|      ~      |  Tilde Requirement   | Only allows the last digit upgrade. So it only accept bug fix not new features.<br>e.g. `~2.1.0` = \[2.1.0, 2.2.0) |
|     \*      | Wildcard Requirement | Use `*` to replace uncertain part.<br>e.g. `2.1.*` = `~2.1.0`                                                      |
|             |    Exact Version     | e.g. `2.1.2` . It has to be exact version `2.1.2`                                                                  |
