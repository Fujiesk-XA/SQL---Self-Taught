

(div/)Simple linear regression =
(div/)VAR Known =
(div/)    FILTER (
(div/)        SELECTCOLUMNS (
(div/)            ALLSELECTED ( Table[Column] ),
(div/)            "Known[X]", [Measure X],
(div/)            "Known[Y]", [Measure Y]
(div/)        ),
(div/)        AND (
(div/)            NOT ( ISBLANK ( Known[X] ) ),
(div/)            NOT ( ISBLANK ( Known[Y] ) )
(div/)       )
(div/)    )
(div/)VAR SlopeIntercept =
(div/)    LINESTX(Known, Known[Y], Known[X])
(div/)VAR Slope =
(div/)    SELECTCOLUMNS(SlopeIntercept, [Slope1])
(div/)VAR Intercept = 
(div/)    SELECTCOLUMNS(SlopeIntercept, [Intercept])
(div/)RETURN
(div/)    Intercept + Slope * [Measure X]
