

Simple linear regression =
VAR Known =
    FILTER (
        SELECTCOLUMNS (
            ALLSELECTED ( Table[Column] ),
            "Known[X]", [Measure X],
            "Known[Y]", [Measure Y]
        ),
        AND (
            NOT ( ISBLANK ( Known[X] ) ),
            NOT ( ISBLANK ( Known[Y] ) )
        )
    )
VAR SlopeIntercept =
    LINESTX(Known, Known[Y], Known[X])
VAR Slope =
    SELECTCOLUMNS(SlopeIntercept, [Slope1])
VAR Intercept = 
    SELECTCOLUMNS(SlopeIntercept, [Intercept])
RETURN
    Intercept + Slope * [Measure X]
